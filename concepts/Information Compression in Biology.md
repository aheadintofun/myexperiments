# Information Compression in Biology

## Definition
At every biological scale, systems compress high-dimensional information into lower-dimensional representations. The key insight: **the compression itself IS the biology**—not a computational convenience, but the fundamental mechanism.

## Compression Hierarchy
Each level is a learned compression of the level below:

$$\text{Genome} \xrightarrow{\text{transcription}} \text{Transcriptome} \xrightarrow{\text{translation}} \text{Proteome} \xrightarrow{\text{function}} \text{Phenome}$$

At each step:
- Information is **filtered** (which genes/proteins matter here?)
- Dimensionality is **reduced** (20,000 genes → hundreds of active pathways)
- Context determines **what to keep** (tissue-specific, stimulus-specific)

## Examples Across Scales

### Gene Regulatory Networks
20,000 genes → key transcription factors → core regulatory circuits:
- Master regulators compress complex expression patterns
- Network motifs (feed-forward, feedback) are compression algorithms
- Cell type identity encoded in ~10-100 key factors

### Immune Repertoire
$10^{15}$ possible TCR/BCR sequences → $10^{8}$ realized → $10^{3}$ dominant clones:
- Thymic selection compresses to self-tolerant repertoire
- Antigen exposure further compresses to memory
- Repertoire is a **compressed model of pathogen space**

### Clinical Diagnosis
High-dimensional phenotype → diagnostic category:
- Thousands of potential symptoms/signs/test results
- Compressed to disease label via clinical decision trees
- Lossy but actionable compression

### Population Genetics
Genomic variation → breeding values:
- Millions of SNPs → polygenic scores
- Genomic estimated breeding values (GEBV) compress heritability
- Compression enables prediction and selection

### Neural Representations
Sensory input → internal representations:
- Retinal photoreceptor activation → edge detectors → object categories
- Biological neural networks learn efficient codes
- Compression maximizes information while minimizing resources

## Computational Parallel
This maps directly to machine learning:
- **Autoencoders**: Compress to latent space, then decode
- **Embeddings**: Gene2vec, protein embeddings, cell embeddings
- **Dimensionality reduction**: PCA, UMAP, t-SNE reveal compressed structure
- **Foundation models**: Pre-trained representations compress biological knowledge

## Key Insight
The compression is **not arbitrary**—it preserves task-relevant information while discarding noise. Different biological contexts use different compression schemes because they care about different features.

## Related Concepts
- [[Hierarchical Composition]] - Compression occurs at each hierarchical transition
- [[Degeneracy in Biological Systems]] - Multiple inputs compress to same output
- [[Variant-Phenotype Mapping]] - Compression from sequence to function
- [[Trajectory and Branching Fate]] - Trajectory through compressed latent space
- [[Context Conditionality]] - Context determines compression scheme

## Tags
#information-theory #dimensionality-reduction #representation-learning #gene-regulation #compression #embeddings #latent-space
