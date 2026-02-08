# Single-Cell Foundation Models

## Definition
Transformer-based neural networks trained on millions of single-cell transcriptomic profiles to learn a universal representation of cell states. These models enable **in silico biology**—simulating genetic perturbations, predicting cell fate transitions, and annotating cell types without wet-lab experiments.

## Computational Structure
The mapping from gene expression to cell state:
$$\text{Gene Expression Vector} \xrightarrow{\text{transformer}} \text{Cell State Embedding}$$

Input: Ranked gene expression (top 2000-5000 genes per cell)
Output: 512-1024 dimensional embedding capturing cell type, state, trajectory position

## Core Models (2023-2026)

### scGPT (2024)
- **Architecture**: GPT-style autoregressive transformer
- **Training**: 10M+ cells from Human Cell Atlas, Tabula Sapiens
- **Context**: Gene-gene co-expression patterns across cell types
- **Emergent capability**: Predicts effects of gene knockouts never seen in training

### Geneformer (2023)
- **Architecture**: BERT-style masked gene prediction
- **Training**: Ranked gene expression (network-based ordering)
- **Insight**: Gene order matters—transcription factors first, downstream targets later
- **Use**: Dosage sensitivity, haploinsufficiency prediction

## Applications

### Cell Type Annotation
**Problem**: You have 100k unlabeled cells from a tumor biopsy. What cell types are present?

**Classical approach**: Manually curate marker genes, build decision trees.

**Foundation model approach**:
1. Embed all cells using scGPT
2. Project onto reference atlas embeddings
3. Transfer labels from nearest neighbors
4. **Speed**: 100k cells annotated in minutes vs. days of manual curation

### In Silico Perturbation
**Problem**: What happens if we delete gene X in cell type Y?

**Classical approach**: CRISPR knockout screen (months, expensive).

**Foundation model approach**:
1. Take cell embedding for type Y
2. Zero out gene X expression
3. Pass perturbed expression through model
4. Predict resulting cell state
5. **Validation**: Predictions correlate with actual CRISPR screens (R > 0.7)

### Trajectory Inference
**Problem**: Cells transition through states (development, differentiation, disease progression). What are the paths?

**Foundation model embedding space = trajectory space**:
- Smooth paths through embedding space = biological trajectories
- Branching points = cell fate decisions
- Distance in embedding space = transcriptomic similarity

### Drug Response Prediction
**Problem**: Will this drug affect cancer cell viability?

**Workflow**:
1. Embed cancer cells before drug treatment
2. Embed cells after drug treatment
3. Direction in embedding space = drug effect signature
4. Transfer to new cancer types to predict sensitivity

## Key Architectural Insight
Unlike protein language models (which treat sequences as tokens), single-cell models treat **genes as tokens**:
- Token vocabulary = ~20,000 genes
- Each cell = sequence of expressed genes (ranked by expression level)
- Self-attention learns gene-gene regulatory interactions

This is a fundamentally different tokenization—**the vocabulary is fixed by biology**.

## Training Data Requirements
Foundation models require **atlases**:
- Human Cell Atlas: >100M cells across all tissues
- Tabula Sapiens: 500k cells, 24 tissues, fully annotated
- Disease atlases: Cancer Cell Line Encyclopedia, tumor atlases

**Challenge**: Batch effects, technical variation across datasets. Models must learn biology-invariant representations.

## Hardware Requirements

### Mac M4 (32GB)
✅ **Excellent platform** for scGPT:
- MPS (Metal Performance Shaders) acceleration
- 32GB RAM handles 100k cell datasets easily
- Inference: 10k cells/minute on M4 Max
- **Advantage over Colab**: No runtime disconnects, local data privacy

### Cloud/Colab
- Needed for fine-tuning (requires GPU memory for gradient updates)
- Inference can run on CPU but slower

## Key Insight
Single-cell foundation models **compress the human cell atlas** into a learned embedding space. This space has biological meaning:
- Distances = transcriptomic similarity
- Directions = gene programs (proliferation, differentiation, stress response)
- Neighborhoods = cell type clusters

Asking the model a question is **asking the atlas** what it knows about that cell state.

This is [[Information Compression in Biology]] applied to the entire cellular landscape.

## Comparison to Bulk RNA-seq
| Dimension | Bulk RNA-seq | Single-cell |
|-----------|--------------|-------------|
| Resolution | Population average | Individual cells |
| Data per sample | 1 vector (20k genes) | 100k vectors (20k genes each) |
| Heterogeneity | Hidden by averaging | Explicitly captured |
| Foundation models | DeepSEA, Enformer (DNA-level) | scGPT, Geneformer (cell-level) |
| Use case | Population-level gene regulation | Cell state trajectories, rare cell types |

## Related Concepts
- [[Foundation Models in Biology]] - General paradigm across biological scales
- [[Information Compression in Biology]] - Cell embeddings compress gene expression space
- [[Trajectory and Branching Fate]] - Trajectories through embedding space
- [[Perturbation-Response-Adaptation]] - In silico perturbations
- [[Multi-Omics Integration]] - Extend to multi-modal cell representations (RNA + ATAC + protein)

## Tags
#single-cell #foundation-models #scgpt #geneformer #cell-atlas #transcriptomics #perturbation #trajectory-inference #embeddings
