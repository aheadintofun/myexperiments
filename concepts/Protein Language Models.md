# Protein Language Models

## Definition
Transformer-based neural networks trained on millions of protein sequences to learn evolutionary patterns and structural constraints. Like language models (BERT, GPT), these models learn representations of proteins without explicit structural supervision—**evolution is the training signal**.

## Computational Structure
The core mapping:
$$\text{Amino Acid Sequence} \xrightarrow{\text{self-supervised learning}} \text{Embedding Vector}$$

Training objective:
- **Masked language modeling**: Predict missing amino acids from context (ESM-2)
- **Generative modeling**: Generate new sequences autoregressively (ESM3, Evo)

## Embedding Hierarchy
Protein language models create multi-scale representations:

### Token-Level Embeddings
Each amino acid → 512-1280 dimensional vector capturing:
- Chemical properties (hydrophobicity, charge)
- Structural propensity (helix, sheet, turn)
- Evolutionary conservation patterns

### Sequence-Level Embeddings
Average/max pool over tokens → single vector per protein:
- Used for protein classification (enzyme family, localization)
- Clustering proteins by function
- Transfer learning for downstream tasks

### Structure-Aware Embeddings
Advanced models (ESM3) jointly learn sequence + structure space:
- Can generate sequences conditioned on structure
- Can predict structure from sequence (ESMFold)
- Unified latent space for both modalities

## Key Models (2022-2026)

### ESM-2 (2022)
- **Training**: 65M-15B parameters, trained on UniRef
- **Use**: Embeddings for zero-shot prediction (solubility, function)
- **Hardware**: Runs on Mac M4 (MPS support), fast inference

### ESM3 (2024-2025)
- **Training**: Sequence + structure co-training
- **Use**: Generative design (can hallucinate new enzymes)
- **Breakthrough**: Generated novel GFP by "simulating 500M years of evolution"
- **Hardware**: Small models on Mac, large models require GPU

### Evo (2025-2026)
- **Training**: DNA sequences (not just proteins)
- **Use**: Genome-scale generation (CRISPR systems, viral vectors)
- **Context**: 131k nucleotides (orders of magnitude larger than ESM)
- **Hardware**: Cloud-only (massive memory requirements)

## Applications

### Zero-Shot Functional Prediction
Input sequence → embedding → predict property without task-specific training:
- Subcellular localization
- Enzyme commission (EC) number
- Protein-protein interaction likelihood
- Disease variant pathogenicity

### Directed Evolution Acceleration
Use embeddings to guide mutagenesis:
- Generate variants predicted to improve stability/activity
- Replace random mutagenesis with model-guided libraries
- 10-100x reduction in library size for same hit rate

### Sequence-Structure Co-Design
ESM3 enables iterative refinement:
1. Specify partial structure constraints
2. Model generates sequence filling gaps
3. Predict structure of generated sequence
4. Iterate until convergence

## Key Insight
Evolution has already performed the experiment of testing billions of sequences across billions of years. Protein language models **compress this evolutionary experiment** into learned representations. This is [[Information Compression in Biology]] applied to the entire protein universe.

## Comparison to Structure Prediction
| Dimension | Structure Prediction | Language Models |
|-----------|---------------------|-----------------|
| Input | Sequence | Sequence |
| Output | 3D coordinates | Embedding vector |
| Training | Structures (PDB, ~200k) | Sequences (UniRef, ~200M) |
| Use | "What does this fold into?" | "What is this similar to?" |
| Speed | Slow (minutes) | Fast (milliseconds) |
| Generative | No (prediction only) | Yes (can generate new sequences) |

## Related Concepts
- [[Protein Structure Prediction]] - Complementary approach via structural modeling
- [[Inverse Folding]] - Can use language model likelihoods for sequence design
- [[Information Compression in Biology]] - Embeddings compress evolutionary information
- [[Variant-Phenotype Mapping]] - Language models predict variant effects
- [[Diffusion-Based Protein Design]] - Alternative generative approach via structure space

## Tags
#protein-language-models #transformers #embeddings #esm #evolution #deep-learning #zero-shot-prediction #generative-models
