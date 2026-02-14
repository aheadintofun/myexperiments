# Notebook 7: Biomedical Image Analysis

**Pathology and radiology image analysis with Python**

Prerequisites: Notebooks 1-6 (sequences, genomics, transcriptomics, protein structure, RNAseq, phylogenetics)

This notebook builds:
1. Digital pathology fundamentals (H&E staining, tissue segmentation)
2. Nuclei detection and counting
3. Texture features (GLCM, Haralick)
4. Radiology image concepts (CT windowing, HU units)
5. Image segmentation (thresholding, watershed)
6. Feature extraction for ML classification
7. Simulated whole-slide image analysis pipeline
8. ROI (Region of Interest) analysis

All images are **synthetically generated** with numpy -- no external image files needed.

Estimated runtime: ~3 minutes on a laptop (all local computation)

**Key learning outcomes:**
1. Understand H&E staining and digital pathology workflows
2. Segment and count cell nuclei computationally
3. Apply CT windowing to visualize different tissue types
4. Extract texture and shape features for machine learning
5. Build a complete image analysis pipeline from pixels to features

---

## Section 0: Setup

We use **scikit-image** for image processing, **scipy** for morphological operations,
and **matplotlib** for visualization. All images are generated synthetically with numpy,
so no external files or downloads are required.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import ndimage
from scipy.spatial.distance import cdist
from skimage import filters, segmentation, measure, morphology, feature, color
from skimage.draw import disk, ellipse
from skimage.feature import graycomatrix, graycoprops
from sklearn.decomposition import PCA
from sklearn.cluster import KMeans
import warnings
warnings.filterwarnings('ignore')
print("Ready -- numpy, scipy, scikit-image, sklearn, matplotlib")
```

---

## Section 1: Digital Pathology Fundamentals

Digital pathology converts glass slides into high-resolution digital images.
H&E (Hematoxylin & Eosin) staining is the gold standard:

- **Hematoxylin** (blue/purple): stains nuclei (DNA-binding)
- **Eosin** (pink): stains cytoplasm and extracellular matrix

A typical whole-slide image is 50,000 x 100,000 pixels at 40x magnification.
Analysis happens on tiles (patches) extracted from regions of interest.

Reference [[Hierarchical Composition]] -- tissue has a multi-scale hierarchy:
molecules -> organelles -> cells -> tissues -> organs.

The computational challenge: extract biologically meaningful features from pixels.
This bridges [[Information Compression in Biology]] -- reducing millions of pixels
to a handful of diagnostic features.

```python
# Generate a synthetic H&E-stained tissue image (256x256 RGB)
np.random.seed(42)
size = 256

# Background (pink eosin-stained stroma)
image = np.zeros((size, size, 3))
image[:, :, 0] = 0.85 + np.random.normal(0, 0.03, (size, size))
image[:, :, 1] = 0.70 + np.random.normal(0, 0.03, (size, size))
image[:, :, 2] = 0.75 + np.random.normal(0, 0.03, (size, size))

# Add nuclei (dark purple circles) and fibroblast nuclei
# ... generates 60 round nuclei + 20 elongated fibroblasts
```

```python
# Simplified stain separation using color thresholding
od = -np.log10(image + 0.01)  # Optical density
hematoxylin = od[:, :, 2] - 0.5 * od[:, :, 0]  # Nuclei channel
eosin = od[:, :, 0] - 0.3 * od[:, :, 2]         # Cytoplasm channel
```

```python
# Threshold the hematoxylin channel to find nuclei (Otsu's method)
threshold = filters.threshold_otsu(hematoxylin)
nuclei_mask = hematoxylin > threshold
nuclei_mask = morphology.remove_small_objects(nuclei_mask, min_size=30)
nuclei_mask = ndimage.binary_fill_holes(nuclei_mask)
labeled = measure.label(nuclei_mask)
regions = measure.regionprops(labeled)
```

---

## Section 2: Nuclear Morphometry

Nuclear morphometry measures the size, shape, and texture of cell nuclei.
Abnormal nuclear features are hallmarks of cancer:

- Enlarged nuclei (increased DNA content)
- Irregular shape (pleomorphism)
- Increased N:C ratio (nucleus:cytoplasm)

Key features used in pathology grading:

$$\text{Circularity} = \frac{4\pi \cdot \text{Area}}{\text{Perimeter}^2}$$

A perfect circle has circularity = 1.0. Cancer nuclei typically have lower values.

Reference [[Quality Control in Living Systems]] -- normal cells maintain strict size
and shape constraints; cancer cells lose this quality control.

```python
# Extract features for each detected nucleus
features_list = []
for region in regions:
    features_list.append({
        'area': region.area,
        'perimeter': region.perimeter,
        'eccentricity': region.eccentricity,
        'solidity': region.solidity,
        'mean_intensity': region.mean_intensity,
        'circularity': 4 * np.pi * region.area / (region.perimeter ** 2 + 1e-10),
    })
```

---

## Section 3: Radiology Image Analysis

Radiology images (CT, MRI, X-ray) use different physics than pathology:

- **CT**: X-ray attenuation in Hounsfield Units (HU). Air = -1000, Water = 0, Bone = +1000
- **MRI**: Magnetic resonance signal intensity (arbitrary units)
- **X-ray**: Projection imaging (2D shadow of 3D anatomy)

"Windowing" adjusts contrast to visualize specific tissues. The same raw data
reveals completely different anatomy depending on the window settings.

Reference [[Signal Processing in Biological Systems]] -- windowing is a form of
signal filtering that extracts task-relevant information from a shared data source.

```python
def apply_window(img, center, width):
    """Apply CT window (center/width) to HU image."""
    low = center - width / 2
    high = center + width / 2
    windowed = np.clip(img, low, high)
    windowed = (windowed - low) / (high - low)
    return windowed

# Common CT windows
windows = {
    'Lung': (-600, 1500),
    'Mediastinum': (40, 400),
    'Bone': (400, 1500),
    'Soft Tissue': (40, 80),
}
```

```python
# Tissue classification from Hounsfield Units
tissue_map = np.zeros((size_ct, size_ct), dtype=int)
tissue_map[ct_image < -500] = 0   # Air
tissue_map[(ct_image >= -500) & (ct_image < -50)] = 1  # Fat/Lung
tissue_map[(ct_image >= -50) & (ct_image < 100)] = 2   # Soft tissue
tissue_map[ct_image >= 100] = 3   # Bone
```

---

## Section 4: Image Segmentation Pipeline

Segmentation separates structures of interest from background. Methods:

- **Thresholding**: simple intensity cutoff (Otsu's method)
- **Watershed**: separates touching objects using topology
- **Deep learning**: U-Net, nnU-Net (not covered here, requires GPU)

The watershed algorithm treats the image as a topographic surface. It "floods"
from local minima (markers) and builds barriers where different flood basins meet.

Reference [[Figure-Ground Decomposition]] -- segmentation is the computational
analog of perceptual figure-ground separation.

```python
# Distance transform for watershed
binary = touch_img > 0.3
distance = ndimage.distance_transform_edt(binary)
local_max = feature.peak_local_max(distance, min_distance=10, labels=binary)
markers = np.zeros_like(binary, dtype=int)
for i, (y_m, x_m) in enumerate(local_max):
    markers[y_m, x_m] = i + 1
labels_ws = segmentation.watershed(-distance, markers, mask=binary)
```

```python
# Lung nodule detection: find dense spots inside lung regions
lung_region = ct_image < -400
lung_region = morphology.remove_small_objects(lung_region, min_size=500)
lung_region_dilated = ndimage.binary_dilation(lung_region, iterations=5)
dense_in_lung = (ct_image > -100) & lung_region_dilated
```

---

## Section 5: Feature Extraction for ML

Machine learning on medical images requires features. Two approaches:

1. **Handcrafted**: texture (GLCM), shape (morphometry), intensity statistics -- interpretable
2. **Learned**: CNN features from pretrained networks -- more powerful but less interpretable

The Gray-Level Co-occurrence Matrix (GLCM) captures texture by counting how often
pairs of pixel intensities occur at specific spatial relationships. Haralick features:

- **Contrast**: intensity difference between neighboring pixels
- **Homogeneity**: closeness of pixel pair distribution to the GLCM diagonal
- **Energy**: sum of squared GLCM elements (uniformity)
- **Correlation**: linear dependency between neighboring pixels

Reference [[Information Compression in Biology]] -- feature extraction compresses
images into biologically meaningful representations.

```python
def compute_texture_features(patch):
    """Compute GLCM-based texture features from a grayscale patch."""
    patch_uint8 = (patch * 255).astype(np.uint8)
    glcm = graycomatrix(patch_uint8, distances=[1, 3],
                        angles=[0, np.pi / 4, np.pi / 2],
                        levels=256, symmetric=True, normed=True)
    features = {}
    for prop in ['contrast', 'dissimilarity', 'homogeneity', 'energy', 'correlation']:
        values = graycoprops(glcm, prop)
        features[prop] = values.mean()
    return features
```

---

## Section 6: Simulated Whole-Slide Image Analysis

Whole-slide images (WSI) are too large to process at once (50,000 x 100,000 pixels).
The standard approach:

1. **Tissue detection**: find tissue regions at low magnification
2. **Tiling**: extract overlapping patches at high magnification
3. **Per-tile analysis**: run feature extraction or deep learning on each tile
4. **Aggregation**: combine tile-level results into slide-level predictions

This is a natural application of [[Hierarchical Composition]] -- information flows
from pixels to patches to slide-level diagnosis.

Reference [[Tissue Topology]] -- the spatial arrangement of cell types within
tissue carries diagnostic information beyond individual cell features.

```python
# Tile the WSI and compute nuclear density per tile
tile_size = 64
stride = 64
for y_tile in range(0, wsi_size - tile_size + 1, stride):
    for x_tile in range(0, wsi_size - tile_size + 1, stride):
        tile_mask = nuc_mask_wsi[y_tile:y_tile + tile_size, x_tile:x_tile + tile_size]
        nuc_density = tile_mask.mean()
        # ... aggregate per-tile features
```

---

## Section 7: ROI Analysis and Feature Aggregation

Region of Interest (ROI) analysis combines spatial information with feature
extraction. Aggregation strategies for slide-level prediction:

- **Mean pooling**: average features across all tiles
- **Max pooling**: take the "worst" (most abnormal) tile
- **Multiple Instance Learning (MIL)**: learn which tiles matter

This connects to [[Selective Catabolism]] -- the system selectively processes
the most informative regions rather than treating all tissue equally.

---

## Summary

| Concept | What you built | Why it matters |
|---------|---------------|----------------|
| H&E simulation | Synthetic tissue image | [[Hierarchical Composition]] in tissue |
| Stain deconvolution | H&E channel separation | Isolate nuclear vs cytoplasmic signal |
| Nuclear segmentation | Otsu + morphology | Count and characterize cells |
| Morphometry | Area, shape, intensity features | Cancer grading criteria |
| CT windowing | HU visualization | Same data, different views |
| Tissue classification | HU-based segmentation | Automated anatomy parsing |
| Watershed | Touching object separation | [[Figure-Ground Decomposition]] |
| GLCM texture | Statistical texture features | ML input for classification |
| WSI pipeline | Tile-based analysis | Scalable digital pathology |
| ROI analysis | Feature aggregation | [[Selective Catabolism]] in diagnostics |

**The complete series:**
- [[01_Sequence_Analysis_Fundamentals]] -- Biopython, the Central Dogma
- [[02_Genomic_Variant_Analysis]] -- Population genetics, GWAS
- [[03_Single_Cell_Transcriptomics]] -- scanpy, cell type discovery
- [[04_Protein_Structure_Drug_Discovery]] -- Structure and drug design
- [[05_Bulk_RNAseq_Differential_Expression]] -- Differential expression analysis
- [[06_Phylogenetics_Evolution]] -- Evolutionary analysis
- [[07_Biomedical_Image_Analysis]] -- Pathology and radiology (this notebook)

**Next**: [[08_Plant_Biology_Agricultural_Genomics]] -- crop science and agricultural applications
