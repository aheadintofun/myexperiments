# Computational Biology Tools Hub

## Conceptual Overview

Biology has entered the **computational era**. Predicting protein structures, designing novel enzymes, analyzing single-cell atlases, and modeling disease progression all rely on sophisticated computational methods.

The unifying thread: **from prediction to generation**. Early computational biology focused on predicting natural structures and functions. Modern methods **generate** novel entities—proteins that never existed, drugs that bind targets with designed specificity, cell types with engineered behaviors.

## Paradigm Evolution

```
           COMPUTATIONAL BIOLOGY PARADIGM SHIFT

    ┌──────────────────────────────────────────────┐
    │  PREDICTION ERA (pre-2020)                   │
    │  "What structure does this sequence fold?"   │
    │  • Homology modeling                         │
    │  • Physics-based simulation                  │
    │  • Pattern recognition                       │
    └──────────────────────────────────────────────┘
                        │
                        │ Deep Learning + Foundation Models
                        │
                        ▼
    ┌──────────────────────────────────────────────┐
    │  GENERATION ERA (2020-present)               │
    │  "Design a protein that does X"              │
    │  • Inverse folding                           │
    │  • Diffusion models                          │
    │  • Protein language models                   │
    │  • De novo design                            │
    └──────────────────────────────────────────────┘
```

**[[Prediction-to-Generation Paradigm Shift]]** - The transition from modeling what exists to designing what could exist.

## Protein Structure and Design

### Structure Prediction: The Solved Problem
**[[Protein Structure Prediction]]** - Computing 3D coordinates from amino acid sequence. AlphaFold 2 (2021) achieved experimental accuracy. Now a **lookup problem**—200M+ structures in databases.

Key models:
- **AlphaFold 2/3**: MSA + deep learning → atomic coordinates
- **ESMFold**: Single-sequence (no MSA) → fast structure prediction
- **Boltz-1, Chai-1**: Multi-chain complexes, protein-ligand binding

Mathematical structure:
$$\text{Sequence} \xrightarrow{\text{neural network}} \text{3D Structure}$$

Accuracy: RMSD < 2Å for most domains. Bottleneck shifted from "Can we predict?" to "What to do with predictions?"

### Inverse Folding: From Structure to Sequence
**[[Inverse Folding]]** - Design sequences that fold to target structure. Reverses the folding problem.

$$\text{Target Structure} \xrightarrow{\text{ProteinMPNN}} \text{Candidate Sequences}$$

Applications:
- Stabilize existing proteins
- Graft binding sites onto scaffolds
- Design protein-protein interfaces

### Generative Design: Novel Backbones
**[[Diffusion-Based Protein Design]]** - Generate completely new protein structures. RFdiffusion samples protein structure space via diffusion models.

Workflow:
1. Sample random structure from noise
2. Iteratively denoise to valid protein geometry
3. Run inverse folding to get sequences
4. Validate with structure prediction + experiment

Enables:
- Binders to arbitrary targets
- Scaffolds for vaccines (stem immunogens)
- Enzymes with novel active sites

### Molecular Docking: Predicting Binding
**[[Molecular Docking]]** - Predict how small molecules bind protein pockets.

Classical methods:
- AutoDock, Vina: Grid-based search + scoring
- Hours per ligand, limited accuracy

Modern methods:
- AlphaFold 3, Chai-1: Joint protein-ligand structure prediction
- DiffDock: Diffusion models for pose generation
- Fast, more accurate

## Foundation Models: Learning from Evolution

### Protein Language Models
**[[Protein Language Models]]** - Transformers trained on protein sequences learn evolutionary patterns.

Key insight: **Evolution is the training signal**. Billions of years of natural experiments compressed into learned representations.

Models:
- **ESM-2** (2022): 65M-15B parameters, embeddings for zero-shot prediction
- **ESM3** (2024): Sequence + structure co-training, generative design
- **Evo** (2025): DNA sequences, genome-scale generation

Applications:
- Zero-shot functional prediction (localization, enzyme class)
- Variant effect prediction (AlphaMissense)
- Directed evolution guidance (reduce library size 10-100x)

Mathematical structure:
$$\text{Sequence} \xrightarrow{\text{transformer}} \text{Embedding Vector}$$

Embedding captures:
- Chemical properties (hydrophobicity, charge)
- Structural propensity (helix, sheet, turn)
- Evolutionary conservation

See [[Information Compression in Biology]]—embeddings compress protein universe.

### Single-Cell Foundation Models
**[[Single-Cell Foundation Models]]** - Transformers trained on cell atlas data (millions of cells).

Models:
- **scGPT**: Gene expression → cell type, perturbation response
- **Geneformer**: Rank-based encoding, transfer learning
- **CellLM**: Multi-species, multi-tissue pre-training

Applications:
- Cell type annotation
- Perturbation prediction (what happens if gene X knocked out?)
- Drug response prediction
- Trajectory inference (developmental paths)

Input representation:
$$\text{Cell} = \{(\text{gene}_i, \text{count}_i)\}_{i=1}^{20000}$$

Transformer learns context-dependent gene interactions.

### Variant Effect Prediction
**[[Variant Effect Prediction]]** - Predict pathogenicity of genetic variants.

Approaches:
- **Conservation**: SIFT, PolyPhen (evolutionary constraint)
- **Structure**: FoldX, Rosetta (stability change)
- **Language models**: AlphaMissense, ESM-1v (learned patterns)

AlphaMissense (2023):
- Trained on AlphaFold structures + MSAs
- Predicts all possible missense variants (71M)
- Matches experimental data (0.9+ AUROC)

Enables:
- Clinical variant interpretation (VUS classification)
- Therapeutic target validation
- Understanding disease mechanisms

## Visualization and Communication

**[[Molecular Biology Visualization]]** - Tools for rendering, animating, and explaining biological structures.

### 3D Structure Visualization
- **PyMOL**: Publication-quality protein renderings
- **NGLview**: Interactive web-based viewer (Jupyter notebooks)
- **ChimeraX**: Volume data, cryo-EM, molecular dynamics

### Animated/Explanatory
- **Molecular Nodes**: Blender-based protein animations
- **Manim**: Mathematical/algorithmic animations (3Blue1Brown style)

### Genomics & Single-Cell
- **Scanpy**: Single-cell analysis and UMAP plots
- **pyGenomeTracks**: Genomic browser tracks
- **IGV**: Interactive genome viewer

Key principle: **Visual communication scales understanding**. Complex mechanisms become intuitive with good visualization.

## Integration Frameworks

### Multi-Omics Integration
**[[Multi-Omics Integration]]** - Fusing genomics, transcriptomics, proteomics, metabolomics.

Challenge: Heterogeneous data types, different scales, missing data.

Approaches:
- **Concatenation**: Stack data matrices (assumes independence)
- **Joint embedding**: Learn shared latent space (MOFA, totalVI)
- **Graph-based**: Knowledge graphs linking entities

Mathematical structure:
$$P(\text{phenotype} \mid \text{genome}, \text{transcriptome}, \text{proteome}) > P(\text{phenotype} \mid \text{genome})$$

Integration provides complementary information.

### Knowledge Graphs
**[[Knowledge Graph as Biological Substrate]]** - Unified representation of genes, proteins, diseases, drugs, pathways.

Entities (nodes):
- Genes, proteins, variants
- Diseases, phenotypes
- Drugs, compounds
- Pathways, ontologies

Relationships (edges):
- Protein-protein interaction
- Gene-disease association
- Drug-target binding
- Pathway membership

Applications:
- Link prediction (find missing gene-disease edges)
- Embedding learning (TransE, ComplEx)
- Multi-hop reasoning (drug repositioning)

## Democratization: Open Weights Movement

**[[Open Weights Movement]]** - Releasing trained model weights enables global access.

Contrast:
- **Closed**: API-only access (cost, control, black box)
- **Open weights**: Download and run locally (free, transparent, modifiable)

Impact:
- Academic labs can use SOTA models
- Low-resource countries access cutting edge
- Community fine-tuning and specialization
- Reproducibility and trust

Examples:
- ESM-2, ESMFold (Meta AI)
- RFdiffusion (University of Washington)
- AlphaMissense (DeepMind)

Enables: Running on local hardware (Mac M4 for ESM-2, cloud for large models).

## Computational Infrastructure

### Hardware Requirements

| Model | Parameters | Hardware | Inference Speed |
|-------|-----------|----------|-----------------|
| **ESM-2 (650M)** | 650M | Mac M4 (MPS) | <1s per protein |
| **ESMFold** | 650M | Mac M4 | ~10s per protein |
| **AlphaFold 2** | ~100M | GPU (8GB VRAM) | 1-10 min per protein |
| **ESM3 (large)** | 15B | Multi-GPU (40GB+) | Minutes per design |
| **Evo** | 7B | Cloud (131k context) | Genome-scale generation |

### Software Ecosystems

**Python-based**:
- Structure: Biopython, PyMOL, MDAnalysis
- ML: PyTorch, JAX, Hugging Face Transformers
- Single-cell: Scanpy, Seurat (R), CellRanger
- Genomics: pysam, cyvcf2, scikit-bio

**Web-based**:
- AlphaFold Server (no installation)
- ESMFold API (fast structure prediction)
- Boltz-1, Chai-1 web servers

## Key Insights

1. **Prediction is solved, generation is frontier**: We can predict most structures. Now designing novel ones.

2. **Foundation models compress evolution**: Billions of years of natural experiments → learned representations.

3. **Multi-modal is winning**: Combining sequence, structure, images, text improves all tasks.

4. **Open weights democratize access**: Local execution on consumer hardware (Mac M4 runs ESM-2).

5. **Visualization scales understanding**: Complex biology intuitive with good rendering.

## Design Patterns

### Pattern 1: Pre-train, then Fine-tune
Train large model on broad data, adapt to specific task:
- ESM-2 on UniRef → fine-tune for stability prediction
- scGPT on cell atlas → fine-tune for drug response

### Pattern 2: Iterative Refinement
Generate candidates, filter, refine:
1. Diffusion model generates protein backbone
2. Inverse folding designs sequences
3. Structure prediction validates designs
4. Experimental testing (top candidates)

### Pattern 3: Multi-Scale Modeling
Combine models across scales:
- Molecular dynamics (atomistic)
- Coarse-grained (residue-level)
- Lattice (tissue-level)

See [[Multi-Scale Lattice]] and [[Hierarchical Composition]].

### Pattern 4: Ensemble Methods
Combine predictions from multiple models:
- Consensus increases accuracy
- Diversity captures uncertainty
- Vote or average predictions

## Related Hubs
- [[Genotype-to-Phenotype Hub]] - Computational prediction of variant effects
- [[Biological Dynamics Hub]] - Simulation of temporal evolution
- [[Lattice and Spatial Modeling Hub]] - Spatial simulation frameworks

## Tags
#hub #computational-biology #structure-prediction #foundation-models #protein-design #machine-learning #alphafold #esm #diffusion-models #visualization #open-weights
