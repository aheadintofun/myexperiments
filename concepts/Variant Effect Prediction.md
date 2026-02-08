# Variant Effect Prediction

## Definition
The computational problem of predicting the phenotypic consequences of genetic variants (SNPs, indels, structural variants) without experimental validation. Critical for precision medicine (rare disease diagnosis), cancer genomics (driver mutations), and population genetics (GWAS interpretation).

## Computational Structure
The prediction function:
$$P(\text{phenotype} \mid \text{variant}, \text{genomic context})$$

Where genomic context includes:
- Local sequence (±1kb to ±1Mb around variant)
- Epigenetic state (chromatin accessibility, histone marks)
- Gene regulatory networks
- Evolutionary conservation

## Prediction Hierarchy

### Protein Coding Variants
**Missense variants** (amino acid substitution):
- Classical tools: SIFT, PolyPhen-2 (conservation + structure)
- Modern: AlphaMissense (AlphaFold-based), EVE (evolutionary)
- Accuracy: ~90% for clearly benign/pathogenic, uncertain for 20-30%

**Loss-of-function** (nonsense, frameshift):
- Gene constraint scores (pLI, LOEUF)
- Tissue-specific expression
- Haploinsufficiency prediction (Geneformer)

### Regulatory Variants
**Non-coding variants** (>98% of genome):
- Classical: DeepSEA, Basset (shallow context, <1kb)
- Modern: **Enformer** (2021, 200kb context), **AlphaGenome** (2026, 1Mb context)
- Challenge: Variant may affect enhancer 100kb away from target gene

**Splice variants**:
- SpliceAI: Deep learning on exon-intron boundaries
- Predicts cryptic splice sites, exon skipping

## AlphaGenome Revolution (2026)
Breakthrough: **1 million base pair context window**

**Why it matters**:
- Captures long-range chromatin interactions (promoter-enhancer loops)
- Predicts effects on genes 100kb+ away
- Integrates DNA sequence + epigenetic state predictions

**Example**: A variant in a distal enhancer affects target gene expression:
$$\text{Variant at chr7:100,000} \rightarrow \text{Altered enhancer activity} \rightarrow \text{Gene expression change at chr7:250,000}$$

Previous models (200kb context) missed this. AlphaGenome captures it.

## Training Paradigms

### Conservation-Based
Learn from evolution (SIFT, GERP, PhyloP):
- Variants at conserved positions = likely deleterious
- Limitation: Misses gain-of-function, human-specific constraints

### Structure-Based
Predict effect on protein stability (AlphaMissense):
- Variants disrupting structure = pathogenic
- Limitation: Coding variants only (~1-2% of variants)

### Functional Genomics
Learn from epigenetic data (Enformer, AlphaGenome):
- Train on ENCODE, Roadmap Epigenomics
- Predict chromatin accessibility, histone marks, gene expression
- Variants altering predictions = regulatory impact

## Clinical Workflow
**Problem**: Patient with rare disease, whole-genome sequencing identifies 4M variants. Which one is causal?

**Prioritization cascade**:
1. **Filter**: Keep coding + regulatory variants in disease genes (~1000 candidates)
2. **Score**: AlphaMissense (coding), AlphaGenome (regulatory)
3. **Rank**: Top 10-50 variants flagged for expert review
4. **Validate**: Functional assays (cell lines, animal models)

**Impact**: Reduces candidates from millions to tens in minutes.

## Key Challenge: Pathogenicity Thresholds
Models output continuous scores, but diagnosis requires binary classification:
- **Benign vs. Pathogenic**: Where to draw the line?
- ClinVar labels used for calibration
- Population frequency data (gnomAD) for filtering

**Uncertain variants** (~30%): Score near threshold, clinical significance unclear. These require functional validation.

## Hardware Requirements

### Classical Tools (SIFT, PolyPhen)
- Pre-computed scores in databases (VEP, ANNOVAR)
- Instant lookup, no computation needed

### Deep Learning Models
- **AlphaMissense**: API-based (no local installation)
- **AlphaGenome**: API client on Mac, computation on Google Cloud
- **Enformer**: TensorFlow model, can run locally on GPU

## Key Insight
Variant effect prediction is a **transfer learning problem**:
1. Pre-train on genomic data (sequences, epigenetics, evolution)
2. Fine-tune on labeled variants (ClinVar, functional assays)
3. Generalize to novel variants

Foundation models ([[Foundation Models in Biology]]) excel here because they learn general genomic syntax, then specialize to pathogenicity prediction.

## Comparison Across Scales

| Variant Type | Classical Tool | Modern Tool | Context Window | Accuracy |
|--------------|----------------|-------------|----------------|----------|
| Missense | SIFT | AlphaMissense | Protein structure | 90% |
| Regulatory | DeepSEA | AlphaGenome | 1Mb DNA | 85% |
| Splice | MaxEntScan | SpliceAI | 10kb | 95% |
| Structural | CNV calling | ab initio + ML | Genome-wide | 70% |

## Related Concepts
- [[Variant-Phenotype Mapping]] - The general mapping problem
- [[Foundation Models in Biology]] - AlphaGenome is a foundation model
- [[Protein Structure Prediction]] - AlphaMissense builds on AlphaFold
- [[Information Compression in Biology]] - Variant scores compress functional evidence
- [[Context Conditionality]] - Effect depends on genomic + cellular context

## Tags
#variant-effect #precision-medicine #alphafold #alphagenome #pathogenicity #rare-disease #gwas #regulatory-variants #splice-variants
