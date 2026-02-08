# Genotype-to-Phenotype Hub

## Conceptual Overview

The central question of biology: **How do genetic variants produce functional consequences?** Whether rare disease mutation, cancer neoantigen, immune receptor specificity, or crop yield trait—the fundamental problem is mapping sequence space to phenotype space.

The unifying thread: **the mapping is not deterministic but probabilistic, context-dependent, and compressed at each level**. Information flows from high-dimensional sequence space through structural, functional, and regulatory layers to emergent phenotypes.

## The Canonical Pipeline

```
         GENOTYPE-TO-PHENOTYPE MAPPING CASCADE

    ┌─────────────────────────────────────────────┐
    │  GENOTYPE                                   │
    │  DNA Sequence (3 billion bp)               │
    │  SNPs, indels, CNVs, SVs                   │
    └─────────────────────────────────────────────┘
                        │
                        │ Transcription + Splicing
                        │ (context-dependent)
                        ▼
    ┌─────────────────────────────────────────────┐
    │  TRANSCRIPTOME                              │
    │  mRNA levels (20k genes)                   │
    │  Alternative splicing isoforms             │
    └─────────────────────────────────────────────┘
                        │
                        │ Translation + PTM
                        │ (tissue-specific)
                        ▼
    ┌─────────────────────────────────────────────┐
    │  PROTEOME                                   │
    │  Protein abundance + modifications         │
    │  Localization, complexes                   │
    └─────────────────────────────────────────────┘
                        │
                        │ Folding + Interaction
                        │ (microenvironment)
                        ▼
    ┌─────────────────────────────────────────────┐
    │  STRUCTURE & FUNCTION                       │
    │  3D coordinates, binding, catalysis        │
    └─────────────────────────────────────────────┘
                        │
                        │ Integration across scales
                        │ (emergent)
                        ▼
    ┌─────────────────────────────────────────────┐
    │  PHENOTYPE                                  │
    │  Disease, yield, immunity, morphology      │
    └─────────────────────────────────────────────┘

      Each arrow is:
      • Many-to-many
      • Context-dependent
      • Lossy compression
```

## Fundamental Concepts

### The Mapping Problem
**[[Variant-Phenotype Mapping]]** - The universal biological problem across all domains. Rare disease (ClinVar), cancer (COSMIC), immunity (TCR repertoires), agriculture (GWAS).

Not a function but a **conditional distribution**:
$$P(\text{phenotype} \mid \text{genotype}, \text{context})$$

### Context Determines Outcome
**[[Context Conditionality]]** - Same variant, different phenotype in different contexts. Genetic background, environment, developmental stage, cell type all modulate effect.

Context vector $\mathbf{c}$ includes:
- Genetic background (epistasis)
- Environmental factors
- Developmental timing
- Stochastic noise

### Many-to-One Mapping
**[[Degeneracy in Biological Systems]]** - Multiple genotypes produce equivalent phenotypes. Codon degeneracy, pathway redundancy, distributed robustness.

$$f(\mathbf{g}_1) = f(\mathbf{g}_2) = \cdots = f(\mathbf{g}_n) = \phi$$

Different genotypes $\mathbf{g}_i$ map to same phenotype $\phi$.

### Compression at Each Level
**[[Information Compression in Biology]]** - Each layer compresses the layer below. 3 billion bp → 20k genes → hundreds of active pathways → dozens of cell types → phenotype.

The **compression is the biology**:
- Dimensionality reduction preserves task-relevant information
- Different contexts use different compression schemes
- Foundation models learn these compressions

## Mathematical Foundations

### Sequence Space
The set of all possible genotypes. For genome of length $L$ with alphabet size 4:
$$|\mathcal{G}| = 4^L$$

Impossibly large. Actual genomes occupy tiny fraction. Evolution explores via local mutations.

### Fitness Landscapes
**[[Fitness Landscapes]]** - Map genotypes to fitness. Evolution traverses this landscape via mutation + selection.

$$w = f(\mathbf{g})$$

Rugged landscapes have local optima. Epistasis creates non-additive interactions:
$$w(\mathbf{g}_1 + \mathbf{g}_2) \neq w(\mathbf{g}_1) + w(\mathbf{g}_2)$$

### Additive vs Non-Additive Effects
**Additive**: Variants contribute independently (GWAS assumes this)
$$\phi = \sum_i \beta_i g_i$$

**Non-additive**: Epistasis, dominance, environmental interactions
$$\phi = f(\mathbf{g}, \mathbf{e})$$

Most complex traits are non-additive.

## Computational Approaches

### Variant Effect Prediction
**[[Variant Effect Prediction]]** - Computational prediction of phenotypic consequences from sequence.

Approaches:
- **Conservation-based**: SIFT, PolyPhen (evolutionary constraint)
- **Structure-based**: FoldX, Rosetta (stability change)
- **Language model**: AlphaMissense, ESM-1v (learned representations)

### Integration Across Data Types
**[[Multi-Omics Integration]]** - Fusing genomics, transcriptomics, proteomics, metabolomics to predict phenotype.

Each layer provides partial information:
$$P(\phi \mid \text{DNA}, \text{RNA}, \text{protein}, \text{metabolites}) > P(\phi \mid \text{DNA alone})$$

### Knowledge Graphs
**[[Knowledge Graph as Biological Substrate]]** - Unified representation of entities (genes, proteins, diseases, drugs) and relationships.

Graph structure enables:
- Link prediction (gene-disease associations)
- Multi-hop reasoning (drug repositioning)
- Embedding learning (compress graph into vectors)

## Domain-Specific Applications

### Rare Disease Genetics
**Pipeline**: Patient phenotype (HPO terms) → exome/genome → rare variants → pathogenicity prediction → diagnosis

Challenges:
- Variants of unknown significance (VUS)
- Incomplete penetrance
- Phenotypic heterogeneity

### Cancer Genomics
**Pipeline**: Tumor sequencing → somatic mutations → driver vs passenger → neoantigen prediction → immunotherapy targets

Challenges:
- Intra-tumor heterogeneity
- Clonal evolution under therapy
- Microenvironment context effects

### Immunology
**Pipeline**: TCR/BCR sequence → antigen specificity → immune response phenotype

Challenges:
- Massive sequence diversity ($10^{15}$ possible receptors)
- Context-dependent recognition
- Cross-reactivity, polyspecificity

### Agriculture & Breeding
**Pipeline**: GWAS → QTL mapping → genomic selection → improved cultivar

Challenges:
- Genotype × environment interactions (G×E)
- Polygenic traits (many small-effect loci)
- Heterosis (hybrid vigor)

## Key Insights

1. **The mapping is a graph, not a function**: Many-to-many, branching, context-dependent.

2. **Context is high-dimensional**: Genetic background, environment, development, stochasticity all matter.

3. **Each layer compresses**: Information bottlenecks at transcription, translation, structure, function.

4. **Prediction requires integration**: Sequence alone is insufficient. Need multi-omics, structural, evolutionary data.

5. **Uncertainty is irreducible**: Stochastic noise, incomplete context, emergent interactions.

## Emergent Complexity

### Hierarchical Effects
Variants propagate through levels:
- **Molecular**: Protein stability, binding affinity
- **Cellular**: Pathway flux, signaling dynamics
- **Tissue**: Cell-cell interactions, spatial organization
- **Organism**: Developmental timing, physiology
- **Population**: Frequency dynamics under selection

See [[Hierarchical Composition]] and [[Multi-Scale Lattice]].

### Spatial Context
Phenotype depends on location:
- Same mutation in different cell types → different disease
- Tumor mutation in invasion front vs core → different microenvironment response

See [[Microenvironment Context]].

### Temporal Dynamics
Static genotype, dynamic phenotype:
- Developmental stage changes gene expression programs
- Aging modifies phenotypic penetrance
- Environmental fluctuations shift fitness

See [[Perturbation-Response-Adaptation]] and [[Trajectory and Branching Fate]].

## Selection and Evolution

### Population Genetics View
**[[Clonal Architecture and Selection]]** - Variants compete in populations. Beneficial alleles rise, deleterious fall.

Wright-Fisher model:
$$P(\text{fixation}) \approx 2s$$

For weakly beneficial allele with selection coefficient $s$.

### Context-Dependent Fitness
Fitness is not intrinsic to genotype:
$$s = s(\mathbf{g}, \mathbf{c})$$

Balancing selection: Heterozygote advantage (sickle cell).

Frequency-dependent selection: Rare advantage (immune diversity).

## Therapeutic Implications

### Precision Medicine
Match treatment to genotype:
- Pharmacogenomics (drug metabolism variants)
- Targeted therapy (oncogene-directed drugs)
- Gene therapy (correct causal mutation)

### Resistance Prediction
Anticipate adaptation:
- Cancer: Which mutations will cause drug resistance?
- Infectious disease: Which viral escape mutations?
- Agriculture: Which pests will overcome resistance genes?

See [[Perturbation-Response-Adaptation]].

## Related Hubs
- [[Biological Dynamics Hub]] - Temporal evolution of phenotypes
- [[Lattice and Spatial Modeling Hub]] - Spatial context for variant effects
- [[Computational Biology Tools Hub]] - Prediction and design frameworks

## Tags
#hub #genotype-phenotype #variant-effect #context-dependence #degeneracy #compression #fitness-landscapes #epistasis #multi-omics #precision-medicine
