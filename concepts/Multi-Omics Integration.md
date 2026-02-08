# Multi-Omics Integration

## Definition
Fusing heterogeneous data types—genome, transcriptome, proteome, epigenome, metabolome—to achieve a systems-level understanding. All biological domains require this integration, making it a universal computational challenge.

## The Integration Problem
Each omics layer provides partial information:
- **Genome**: Potential (what could happen)
- **Transcriptome**: Intention (what the cell plans)
- **Proteome**: Reality (what's actually functional)
- **Epigenome**: Regulation (how expression is controlled)
- **Metabolome**: Activity (what's biochemically happening)

Integration reveals **how genotype becomes phenotype** through intermediate layers.

## Cross-Domain Examples

### Cancer
| Layer | Technology | Information |
|-------|-----------|-------------|
| Genome | WGS/WES, CNV | Driver mutations, tumor evolution |
| Transcriptome | scRNA-seq, spatial | Active pathways, cell states |
| Proteome | TMT-MS, RPPA | Functional protein levels, PTMs |
| Epigenome | ATAC-seq, methylation | Regulatory landscape |
| Metabolome | LC-MS metabolomics | Metabolic reprogramming |

### Immunology
| Layer | Technology | Information |
|-------|-----------|-------------|
| Genome | HLA typing, KIR | Antigen presentation capacity |
| Transcriptome | CITE-seq, TCR-seq | Cell states, clonal expansion |
| Proteome | CyTOF, Olink | Surface markers, cytokines |
| Epigenome | ChIP-seq | T helper differentiation programs |
| Metabolome | Immunometabolism | Effector vs memory bias |

### Rare Disease
| Layer | Technology | Information |
|-------|-----------|-------------|
| Genome | Trio WES/WGS | Candidate variants |
| Transcriptome | RNA-seq (tissues) | Splicing defects, expression |
| Proteome | CSF/plasma proteomics | Functional consequences |
| Epigenome | Methylation arrays | Imprinting, regulatory variants |
| Metabolome | IEM screening | Inborn errors of metabolism |

### Agriculture
| Layer | Technology | Information |
|-------|-----------|-------------|
| Genome | GBS, SNP chips | QTL mapping, GWAS |
| Transcriptome | RNA-seq (stress) | Stress response pathways |
| Proteome | Seed proteomics | Storage proteins, enzymes |
| Epigenome | Chromatin accessibility | Regulatory variation |
| Metabolome | Metabolite QTL | Nutritional quality, flavor |

## Integration Tools
**Cross-domain frameworks**:
- **MOFA+**: Multi-omics factor analysis (latent factor models)
- **totalVI**: Integrates RNA + protein from CITE-seq
- **MultiNicheNet**: Cell-cell signaling from multi-omics
- **DIABLO** (mixOmics): Multi-block PLS for multi-omics

**Data structures**:
- **MuData**: Multi-modal AnnData for Python
- **MultiAssayExperiment**: R/Bioconductor multi-omics container
- **Seurat v5**: Bridge integration across modalities

## Computational Challenges
1. **Different scales**: Gene counts (discrete) vs metabolite concentrations (continuous)
2. **Different dimensionalities**: 20K genes, 5K proteins, 500 metabolites
3. **Missing data**: Not all layers measured in all samples
4. **Batch effects**: Technical variation within and across modalities
5. **Causal inference**: Which layer is upstream/downstream?

## Key Insight
The goal is not just **correlation** across layers but **mechanistic understanding**. Which genomic variant causes which transcriptional change, leading to which protein alteration, producing which metabolic phenotype?

This requires **causal multi-omics models**, not just integrative clustering.

## Related Concepts
- [[Variant-Phenotype Mapping]] - Integration reveals genotype-phenotype path
- [[Information Compression in Biology]] - Each omics layer is a compression
- [[Hierarchical Composition]] - Omics layers are hierarchical levels
- [[Context Conditionality]] - Integration reveals context dependencies
- [[Knowledge Graph as Biological Substrate]] - Graph unifies omics layers

## Tags
#multi-omics #data-integration #systems-biology #genomics #transcriptomics #proteomics #metabolomics #epigenomics #MOFA
