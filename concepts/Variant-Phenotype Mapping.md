# Variant-Phenotype Mapping

## Definition
The universal biological problem: how does genotypic variation produce functional consequences? Whether rare disease mutation, tumor neoantigen, immune receptor variant, or crop cultivar trait—the core question is the same.

## Computational Structure
The mapping is fundamentally a graph:
$$\text{Sequence} \rightarrow \text{Structure} \rightarrow \text{Function} \rightarrow \text{Phenotype}$$

Each arrow represents a many-to-many transformation subject to context.

## Domain Examples

### Rare Disease
- Pathogenic variants in OMIM/ClinVar
- Functional prediction via AlphaMissense, SIFT
- Phenotype annotation via HPO (Human Phenotype Ontology)

### Cancer
- Somatic mutations in COSMIC
- Neoantigen prediction for immunotherapy
- Tumor phenotype from histopathology

### Immunology
- TCR/BCR sequence variation
- Antigen recognition specificity
- Immune response phenotype

### Agriculture
- Cultivar trait loci in Gramene, MaizeGDB
- Genomic selection for yield
- Environmental adaptation phenotypes

## Key Insight
This is not a deterministic function but a **conditional probability distribution**:
$$P(\text{phenotype} \mid \text{genotype}, \text{context})$$

The context vector includes genetic background, environment, developmental stage, and stochastic factors.

## Related Concepts
- [[Degeneracy in Biological Systems]] - Multiple genotypes map to same phenotype
- [[Context Conditionality]] - Phenotype depends on context vector
- [[Perturbation-Response-Adaptation]] - Dynamic variant-phenotype mapping
- [[Knowledge Graph as Biological Substrate]] - Variant effect graphs
- [[Multi-Scale Lattice]] - Phenotype emerges across hierarchical scales

## Tags
#genotype-phenotype #variant-annotation #functional-genomics #precision-medicine #systems-biology
