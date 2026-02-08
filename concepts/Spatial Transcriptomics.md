# Spatial Transcriptomics

## Definition
Measurement of **gene expression with spatial resolution**—knowing **what genes are active** and **where in the tissue**. Combines molecular profiling (transcriptomics) with spatial mapping (histology).

## Core Breakthrough
Traditional single-cell RNA-seq loses spatial information (cells dissociated). Spatial transcriptomics preserves tissue architecture while measuring expression.

**Result**: Map cellular states to anatomical locations, reveal tissue organization principles.

## Technologies

### Slide-Based Sequencing
Tissue placed on spatially barcoded surface:
- **10x Genomics Visium**: 55 μm spots, ~10 cells/spot, whole transcriptome
- **Spatial resolution**: Multicellular (spot-level), not single-cell

### Imaging-Based Methods
Fluorescence in situ hybridization (FISH) at scale:
- **seqFISH+**: Sequential hybridization, 10,000+ genes, subcellular resolution
- **MERFISH**: Combinatorial barcoding, multiplexed imaging
- **Single-cell resolution**: See individual cells in tissue context

### In Situ Sequencing
Sequence directly in tissue:
- **Slide-seq**: Bead-based barcoding, 10 μm resolution
- **HDST**: High-definition spatial transcriptomics, 2 μm resolution
- **Approaching single-cell**: Near-cellular resolution

### Emerging: Subcellular Resolution
- **Stereo-seq**: Single-cell and subcellular resolution
- **Xenium (10x)**: Imaging-based, subcellular, 300+ genes
- **CosMx (NanoString)**: 1,000+ genes, subcellular

## Key Insights Enabled

### Tissue Architecture
- **Cell type spatial organization**: Which cell types are neighbors?
- **Tissue domains**: Functional zones (tumor core vs. margin, cortical layers)
- **Spatial niches**: Microenvironments defined by cell type composition

### Cell-Cell Communication
Infer signaling from co-localization:
- **Ligand-receptor pairs**: Which cells express ligands, which express receptors?
- **Spatial proximity**: Are sender and receiver cells adjacent?
- **Directional signaling**: Tissue polarity, gradients (see [[Cross-Boundary Signaling]])

### Development and Morphogenesis
- **Spatial gene expression gradients**: Morphogen patterns (Wnt, Hedgehog, BMP)
- **Developmental zones**: Proliferation vs. differentiation regions
- **Symmetry breaking**: Spatial patterns emerge from uniform tissue (see [[Symmetry Breaking in Biological Systems]], [[Morphogenesis]])

### Disease Spatial Heterogeneity
- **Tumor microenvironment**: Cancer cells, immune cells, stromal cells—spatial arrangement
- **Immune infiltration patterns**: Hot vs. cold tumors, immune exclusion zones
- **Neurodegenerative pathology**: Spatial spread of amyloid plaques, tau tangles

## Computational Analysis

### Spatial Clustering
- **Identify spatial domains**: Cluster spots/cells by expression and proximity
- **Graph-based methods**: Build spatial neighborhood graph (see [[Network Topology]])

### Deconvolution
Decompose multicellular spots into cell type proportions (Visium):
- Reference: Single-cell RNA-seq atlas
- Deconvolution: Infer cell type mixture per spot
- Tools: Cell2location, SPOTlight, RCTD

### Ligand-Receptor Interaction Inference
- **CellPhoneDB**: Infer cell-cell communication from expression
- **NicheNet**: Predict ligand-receptor pairs driving expression patterns
- **Spatial constraint**: Require physical proximity

### Integration with Single-Cell Data
- Single-cell: High molecular resolution, no spatial info
- Spatial: Spatial info, lower molecular resolution (or limited gene panel)
- **Integration**: Map single-cell states onto spatial coordinates

## Visualization
Key challenge: Visualize high-dimensional data in 2D/3D tissue space.

**Tools**:
- **Scanpy**: Spatial plotting functions (spot-level)
- **Seurat**: Spatial feature plots, integrated with scRNA-seq
- **Vitessce**: Interactive spatial visualization
- **Napari**: Python viewer for spatial imaging data

## Biological Questions Addressed

### What defines a niche?
[[Microenvironment Context]]: Spatial transcriptomics reveals niche composition:
- Cell types present
- Signaling molecules active
- Spatial structure (diffuse vs. defined boundaries)

### How do tissues self-organize?
[[Emergent Global Pattern]]: Spatial expression patterns reveal:
- [[Local Interaction]] rules (reaction-diffusion, cell sorting)
- [[Turing Pattern Formation]]: Periodic spatial structures
- [[Hierarchical Composition]]: Multi-scale tissue organization

### How does context determine cell fate?
[[Context Conditionality]]: Same cell type, different location → different state.
- Spatial gradients specify cell fate
- Neighbor identities modulate expression
- Physical position encodes developmental information

## Limitations
- **Resolution trade-offs**: Whole transcriptome but multicellular (Visium) vs. single-cell but limited genes (MERFISH)
- **Cost**: Expensive per sample, limits large cohort studies
- **3D reconstruction**: Most methods 2D sections, 3D requires serial sectioning
- **Fresh vs. fixed tissue**: FFPE compatibility varies

## Future Directions
- **Single-cell, whole transcriptome, subcellular resolution**: The holy grail
- **3D spatial transcriptomics**: Serial sectioning or tissue clearing
- **Multimodal**: Spatial transcriptomics + proteomics + epigenomics
- **Temporal**: Spatial dynamics over time (development, disease progression)

## Related Concepts
- [[Single-Cell Foundation Models]] - Integrate spatial and single-cell data
- [[Microenvironment Context]] - Spatial transcriptomics reveals niches
- [[Cross-Boundary Signaling]] - Infer from spatial co-expression
- [[Context Conditionality]] - Location determines cell state
- [[Morphogenesis]] - Spatial expression patterns during development
- [[Network Topology]] - Cell-cell interaction networks in space
- [[Molecular Biology Visualization]] - Visualizing spatial data

#spatial-transcriptomics #tissue-architecture #microenvironment #cell-cell-communication #imaging #genomics
