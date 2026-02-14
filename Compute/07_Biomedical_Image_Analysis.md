# Notebook 7: Biomedical Image Analysis

**Pathology and radiology image analysis with Python**

Prerequisites: Notebooks 1-6 (sequences, genomics, transcriptomics, protein structure, RNAseq, clinical)

This notebook builds:
1. Digital pathology fundamentals (IHC staining, stain deconvolution)
2. Nuclei detection and counting
3. Texture features (GLCM, Haralick)
4. Radiology image concepts (MRI windowing, tissue segmentation)
5. Image segmentation (thresholding, watershed)
6. Feature extraction for ML classification
7. Whole-slide image (WSI) analysis pipeline with real cancer tissue
8. ROI (Region of Interest) analysis

**Data sources**: Real immunohistochemistry (IHC) colon tissue image (`skimage.data.immunohistochemistry()`), real human mitosis image (`skimage.data.human_mitosis()`) for cell counting and watershed segmentation. Real brain MRI (`skimage.data.brain()`) for windowing and tissue segmentation. Real Aperio whole-slide image (CMU-1-Small-Region.svs, 2220x2967) for the WSI tiling pipeline.

**Data setup**: Run `python data/download_all_data.py` to download the WSI file (~2 MB). The scikit-image built-in datasets require no separate download. Install: `pip install scikit-image openslide-python openslide-bin`.

Estimated runtime: ~3 minutes on a laptop

**Key learning outcomes:**
1. Understand IHC staining and digital pathology workflows
2. Segment and count cell nuclei computationally
3. Apply MRI windowing to visualize different tissue types
4. Extract texture and shape features for machine learning
5. Build a complete WSI tiling pipeline from real cancer tissue

---

## Section 0: Setup

We use **scikit-image** for image processing (including built-in real tissue and brain images), **scipy** for morphological operations, **openslide** for reading whole-slide images, and **matplotlib** for visualization.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import ndimage
from skimage import data, filters, segmentation, measure, morphology, feature, color
from skimage.feature import graycomatrix, graycoprops
from sklearn.decomposition import PCA
from sklearn.cluster import KMeans
import openslide
```

---

## Section 1: Digital Pathology Fundamentals

Digital pathology converts glass slides into high-resolution digital images.
Common staining protocols include:

- **H&E** (Hematoxylin & Eosin): the gold standard for general histology
- **IHC** (Immunohistochemistry): hematoxylin counterstain + DAB for specific proteins

In both protocols, **hematoxylin** (blue/purple) stains nuclei and **eosin/DAB** stains
cytoplasm or specific protein targets. We use a **real IHC colon tissue image** from
scikit-image and apply **HED color deconvolution** to separate stain components.

Reference [[Hierarchical Composition]] -- tissue has a multi-scale hierarchy:
molecules -> organelles -> cells -> tissues -> organs.

```python
# Load real IHC-stained colon tissue image
ihc_rgb = data.immunohistochemistry()  # Real IHC image (512x512x3, uint8)
image = ihc_rgb / 255.0

# HED stain deconvolution
ihc_hed = color.rgb2hed(image)
hematoxylin = ihc_hed[:, :, 0]  # Nuclei (blue/purple)
eosin = ihc_hed[:, :, 1]        # Cytoplasm/stroma (pink)
dab = ihc_hed[:, :, 2]          # DAB protein marker (brown)
```

```python
# Threshold the hematoxylin channel to find nuclei (Otsu's method)
threshold = filters.threshold_otsu(hematoxylin)
nuclei_mask = hematoxylin > threshold
nuclei_mask = morphology.remove_small_objects(nuclei_mask, min_size=30)
nuclei_mask = ndimage.binary_fill_holes(nuclei_mask)
labeled = measure.label(nuclei_mask)
regions = measure.regionprops(labeled, intensity_image=hematoxylin)
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
- **MRI**: Magnetic resonance signal intensity (arbitrary units, tissue-dependent contrast)
- **X-ray**: Projection imaging (2D shadow of 3D anatomy)

"Windowing" adjusts contrast to visualize specific tissues. We demonstrate with
**real brain MRI data** from `skimage.data.brain()` (T1-weighted, 10 axial slices).

Reference [[Signal Processing in Biological Systems]] -- windowing is a form of
signal filtering that extracts task-relevant information from a shared data source.

```python
def apply_window(img, center, width):
    """Apply intensity window (center/width) to radiological image."""
    low = center - width / 2
    high = center + width / 2
    windowed = np.clip(img, low, high)
    windowed = (windowed - low) / (high - low)
    return windowed

brain_volume = data.brain()  # T1-weighted MRI, (10, 256, 256), uint16
mri_slice = brain_volume[5].astype(float)
```

```python
# Multi-Otsu tissue classification
thresholds = filters.threshold_multiotsu(brain_pixels, classes=3)
# Segments into: Background, CSF/dark, Gray matter, White matter
```

---

## Section 4: Image Segmentation Pipeline

Segmentation separates structures of interest from background. Methods:

- **Thresholding**: simple intensity cutoff (Otsu's method)
- **Watershed**: separates touching objects using topology
- **Deep learning**: U-Net, nnU-Net (not covered here, requires GPU)

The watershed algorithm treats the image as a topographic surface using
**real human mitosis fluorescence microscopy** from `skimage.data.human_mitosis()`.

Reference [[Figure-Ground Decomposition]] -- segmentation is the computational
analog of perceptual figure-ground separation.

```python
mitosis_image = data.human_mitosis()  # Grayscale, uint8, 512x512

# Distance transform for watershed
binary = mitosis_float > filters.threshold_otsu(mitosis_float)
distance = ndimage.distance_transform_edt(binary)
local_max = feature.peak_local_max(distance, min_distance=7, labels=binary)
labels_ws = segmentation.watershed(-distance, markers, mask=binary)
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

## Section 6: Whole-Slide Image (WSI) Analysis

Whole-slide images (WSI) are too large to process at once -- a typical 40x scan is
50,000 x 100,000+ pixels (several gigabytes uncompressed). The standard approach:

1. **Tissue detection**: find tissue regions at low magnification
2. **Tiling**: extract overlapping patches at high magnification
3. **Per-tile analysis**: run feature extraction or deep learning on each tile
4. **Aggregation**: combine tile-level results into slide-level predictions

We use a **real Aperio whole-slide image** (CMU-1-Small-Region.svs) read via
**OpenSlide**, the standard library for reading vendor-specific WSI formats.

This is a natural application of [[Hierarchical Composition]] -- information flows
from pixels to patches to slide-level diagnosis.

Reference [[Tissue Topology]] -- the spatial arrangement of cell types within
tissue carries diagnostic information beyond individual cell features.

```python
# Load real WSI via OpenSlide
slide = openslide.OpenSlide("data/nb07/CMU-1-Small-Region.svs")
wsi_region = slide.read_region((0, 0), 0, slide.dimensions)
wsi_image = np.array(wsi_region.convert("RGB")) / 255.0

# Tile and compute nuclear density per tile
tile_size = 256
for y_tile in range(0, h - tile_size + 1, tile_size):
    for x_tile in range(0, w - tile_size + 1, tile_size):
        tile_rgb = wsi_image[y_tile:y_tile + tile_size, x_tile:x_tile + tile_size]
        # Skip background, detect nuclei via HED + Otsu per tile
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
| Real IHC tissue | skimage.data.immunohistochemistry() | [[Hierarchical Composition]] in tissue |
| Stain deconvolution | HED color space separation | Isolate nuclear vs cytoplasmic signal |
| Nuclear segmentation | Otsu + morphology on real tissue | Count and characterize cells |
| Morphometry | Area, shape, intensity features | Cancer grading criteria |
| MRI windowing | Real brain MRI (skimage.data.brain) | Same data, different views |
| Tissue classification | Multi-Otsu brain segmentation | Automated anatomy parsing |
| Watershed | Real cell separation (human mitosis) | [[Figure-Ground Decomposition]] |
| GLCM texture | Statistical texture features | ML input for classification |
| WSI pipeline | Real Aperio cancer tissue (OpenSlide) | Scalable digital pathology |
| ROI analysis | Feature aggregation | [[Selective Catabolism]] in diagnostics |

**The complete series:**
- [[01_Sequence_Analysis_Fundamentals]] -- Biopython, the Central Dogma
- [[02_Genomic_Variant_Analysis]] -- Population genetics, GWAS
- [[03_Single_Cell_Transcriptomics]] -- scanpy, cell type discovery
- [[04_Protein_Structure_Drug_Discovery]] -- Structure and drug design
- [[05_Bulk_RNAseq_Differential_Expression]] -- Differential expression analysis
- [[06_Clinical_Biomedical_Informatics]] -- Clinical data and survival analysis
- [[07_Biomedical_Image_Analysis]] -- Pathology and radiology (this notebook)

**Next**: [[08_Plant_Biology_Agricultural_Genomics]] -- crop science and agricultural applications
