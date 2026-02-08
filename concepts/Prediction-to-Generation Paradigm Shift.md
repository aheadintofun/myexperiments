# Prediction-to-Generation Paradigm Shift

## Definition
The fundamental transition in computational biology (2021-2026) from **modeling what exists** to **designing what could exist**. Early AI models predicted properties of natural biological entities; modern models generate novel entities with specified properties.

## Historical Trajectory

### Phase 1: Prediction (2015-2021)
**Goal**: Accurately model natural biology
- Predict protein structure from sequence (AlphaFold 2)
- Predict gene expression from DNA sequence (Enformer)
- Predict variant pathogenicity (SIFT, PolyPhen)

**Limitation**: Constrained to biological reality. Models answer "What is this?" not "What could this be?"

### Phase 2: Generation (2022-2025)
**Goal**: Design novel biological entities
- Generate protein backbones for specified functions (RFdiffusion)
- Generate sequences for target structures (ProteinMPNN, ESM3)
- Generate CRISPR systems (OpenCRISPR-1, Evo)

**Breakthrough**: Models explore regions of biological space inaccessible to evolution.

### Phase 3: Interaction (2024-2026)
**Goal**: Design context-dependent binding and assembly
- Predict protein-ligand binding (AlphaFold 3, Chai-1)
- Design binders with specified affinity (RFdiffusion → ProteinMPNN → validation)
- Simulate multi-component assemblies (AlphaFold-Multimer, Boltz-1)

**Emergence**: Moving from static structures to dynamic interactions.

## Computational Distinction

### Predictive Models
**Input**: Natural biological entity
**Output**: Property of that entity
**Loss function**: Match experimental ground truth

**Example**: AlphaFold 2
- Input: Protein sequence from UniProt
- Output: 3D structure
- Training: Minimize RMSD to PDB crystals

### Generative Models
**Input**: Desired property or constraint
**Output**: Novel biological entity satisfying constraints
**Loss function**: Likelihood under learned distribution

**Example**: RFdiffusion
- Input: "Design binder to insulin"
- Output: Novel protein backbone (never seen in nature)
- Training: Learn distribution of protein geometries, then sample conditioned on constraint

## The Critical Enabling Shift: Learned Latent Spaces

Generative models require **continuous, meaningful latent spaces**:

$$\text{Biological Entity} \leftrightarrow \text{Latent Vector}$$

**Encoder**: Biological entity → latent vector (compress)
**Decoder**: Latent vector → biological entity (decompress)

**Key property**: Smooth interpolation in latent space produces biologically meaningful intermediates.

### Examples of Latent Spaces
- **ESM-2**: Protein sequences → 1280-dim embedding space
- **scGPT**: Cell gene expression → 512-dim cell state space
- **AlphaFold**: Protein structures → learned geometric representation
- **Evo**: DNA sequences → genomic latent space

**Why this enables generation**: Sample random point in latent space, decode to biological entity. If space is well-structured, decoded entity is functional.

## Application Hierarchy

### Level 1: Property Optimization
**Task**: Improve existing protein (stability, solubility, activity)
**Method**: Encode protein → perturb latent vector → decode → validate
**Tools**: Protein language models (ESM-2) + directed mutagenesis

### Level 2: De Novo Design
**Task**: Create entirely new protein with specified function
**Method**: Specify constraint → sample latent space → generate candidates → filter
**Tools**: RFdiffusion + ProteinMPNN + AlphaFold validation

### Level 3: Multi-Component Systems
**Task**: Design interacting components (binder pairs, enzyme-substrate)
**Method**: Co-design in joint latent space with interaction constraints
**Tools**: AlphaFold 3, Chai-1 (joint modeling)

## Key Insight: The Inverse Problem Structure

All generative tasks are **inverse problems**:

### Forward Problem (Prediction)
$$f: \text{Sequence} \rightarrow \text{Structure}$$
Well-defined, unique output (for proteins).

### Inverse Problem (Generation)
$$f^{-1}: \text{Structure} \rightarrow \text{Sequence}$$
Ill-posed, many valid solutions.

**Generative models solve inverse problems** by:
1. Learning the forward mapping $f$
2. Learning the distribution of inputs $P(\text{sequence})$
3. Sampling from $P(\text{sequence} \mid \text{structure})$ via Bayes rule or diffusion

## Validation Challenge

**The generative bottleneck**: Models can produce biologically impossible outputs that look plausible.

### Multi-Stage Validation Pipeline
1. **In silico**: Does generated sequence fold to intended structure? (AlphaFold)
2. **In silico**: Is binding pose stable? (Molecular dynamics)
3. **In vitro**: Does synthesized protein express and fold? (Wet lab)
4. **In vitro**: Does it bind target with predicted affinity? (SPR, ITC)
5. **In vivo**: Does it function in cells/organisms? (Cell assays, animal models)

**Attrition rate**: ~10-20% success from computational design to validated binder.

## Paradigm Comparison

| Dimension | Predictive Era | Generative Era |
|-----------|----------------|----------------|
| Core task | "What is this?" | "How do I make X?" |
| Training data | Natural proteins, genomes, cells | Same, but learn latent space |
| Model type | Discriminative (classifier, regressor) | Generative (VAE, GAN, diffusion) |
| Output | Property of input | Novel entity satisfying constraint |
| Validation | Compare to experiment | Synthesize and test |
| Application | Understanding biology | Engineering biology |

## Related Concepts
- [[Protein Structure Prediction]] - Predictive paradigm
- [[Diffusion-Based Protein Design]] - Generative paradigm
- [[Inverse Folding]] - Inverse problem for sequences
- [[Protein Language Models]] - Learn generative distributions over sequences
- [[Foundation Models in Biology]] - Enable both prediction and generation
- [[Information Compression in Biology]] - Latent spaces are compressed representations

## Tags
#generative-models #protein-design #inverse-problems #latent-space #paradigm-shift #diffusion-models #de-novo-design #computational-biology
