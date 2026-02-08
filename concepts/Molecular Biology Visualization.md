# Molecular Biology Visualization

Computational tools for rendering biological structures, sequences, and data with emphasis on explanatory and publication-quality output.

## 3D Molecular Structure

| Tool | Use Case | Environment |
|------|----------|-------------|
| **PyMOL** | Publication figures, scriptable | Desktop |
| **NGLview** | Jupyter-native 3D viewer | Notebook |
| **py3Dmol** | Lightweight Jupyter widget | Notebook |
| **ChimeraX** | Cryo-EM, modern UCSF viewer | Desktop |
| **Mol*** (MolStar) | Web-based, smooth animations | Browser |

## Animated / Explanatory (3Blue1Brown Style)

- **Molecular Nodes** - Blender addon for stunning molecular animations. Import PDB, animate dynamics, render video. The closest to "3B1B for molecules." https://github.com/BradyAJohnston/MolecularNodes
- **Manim** - 3B1B's library; can build molecular representations for seamless math+biology explanations
- **CellPAINT** - David Goodsell's watercolor-style molecular cross-sections
- **WEHI Animations** (Drew Berry) - Gold standard inspiration: https://www.wehi.edu.au/wehi-tv

## Sequence & Alignment

- **pyMSAviz** - Multiple sequence alignment visualization
- **Biotite** - Structure/sequence viz with bioinformatics toolkit

## Genomics & Single-Cell

- **Scanpy** - Built-in UMAP, t-SNE, heatmaps for single-cell
- **pyGenomeTracks** - Genome browser-style track plots
- **IGV** - Interactive genome viewer

## Pathways & Networks

- **Cytoscape** + py2cytoscape - Network/pathway graphs
- **PyVis** - Interactive network visualization

## General Scientific Plotting

- **matplotlib + seaborn** - Heatmaps, volcano plots, clustering
- **plotly** - Interactive dashboards

## Key Insight

For M4 Mac workflows: **NGLview** for structures in Jupyter, **Scanpy plotting** for single-cell, **Molecular Nodes + Blender** for animated explanatory content. PyMOL for comparing protein folds from [[Protein Structure Prediction]] tools like Chai-1/Boltz-1.

## Related Concepts

- [[Protein Structure Prediction]]
- [[Single-Cell Foundation Models]]
- [[Information Compression in Biology]]
- [[Foundation Models in Biology]]

#visualization #molecular-biology #tools #blender #pymol
