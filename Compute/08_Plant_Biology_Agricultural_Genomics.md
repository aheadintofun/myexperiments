# Notebook 8: Plant Biology & Agricultural Genomics

**From crop genomes to field phenotypes -- computational approaches to food security**

Prerequisites: Notebooks 1-7 (sequences, genomics, transcriptomics, protein structure, RNAseq, clinical, imaging)

This notebook builds:
1. Plant genome characteristics (polyploidy, TE content, genome size variation)
2. Crop domestication genetics (selective sweeps, bottleneck signatures)
3. GWAS for agricultural traits (yield, drought tolerance, disease resistance)
4. QTL mapping concepts
5. Marker-assisted selection (MAS) simulation
6. Phenotype prediction from genomic data
7. Environmental x Genotype interaction (GxE)
8. Crop diversity and conservation genetics

**Data sources**: Curated crop genome statistics (15 species with genome sizes, ploidy, TE content). Arabidopsis 1001 Genomes-derived SNP data (200 accessions x 1000 SNPs across 5 chromosomes) with flowering time phenotypes. GxE interaction and diversity timeline kept as simulations (real multi-environment trial data not freely available).

**Data setup**: Run `python data/download_all_data.py` from the `Compute/` directory before executing.

Estimated runtime: ~3 minutes

**Key learning outcomes:**
1. Understand how plant genomes differ from animal genomes -- see [[Plant-Animal Divergence]]
2. Simulate and detect domestication bottlenecks and selective sweeps -- see [[Fitness Landscapes]]
3. Run GWAS on crop breeding lines and interpret Manhattan plots -- see [[Variant-Phenotype Mapping]]
4. Build genomic prediction models for yield -- see [[Genotype-to-Phenotype Hub]]
5. Analyze genotype-by-environment interaction -- see [[Context Conditionality]]
6. Quantify genetic erosion and the role of conservation -- see [[Robustness and Evolvability]]

---

## Section 0: Setup

We use the standard scientific Python stack: numpy for simulation, scipy for statistics, sklearn for genomic prediction, pandas for data handling, and matplotlib for visualization. No specialized plant biology libraries are required.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats
from sklearn.linear_model import Ridge
from sklearn.model_selection import cross_val_score
from sklearn.decomposition import PCA
from collections import Counter
import warnings
warnings.filterwarnings('ignore')
print("Ready -- numpy, scipy, sklearn, pandas, matplotlib")
```

---

## Section 1: Plant Genome Characteristics

Plant genomes are dramatically different from animal genomes:

- **Polyploidy**: Many crops are polyploid (wheat = hexaploid 6x, potato = tetraploid 4x)
- **Genome size**: Ranges from 63 Mb (Genlisea) to 150 Gb (Paris japonica) -- 2400x variation!
- **Transposable elements**: Often >80% of genome (maize ~85%)
- **Gene duplication**: Whole-genome duplications (WGD) are common

Reference [[Degeneracy in Biological Systems]] -- polyploidy creates massive functional redundancy. Multiple copies of every gene means the system can tolerate mutations, explore new functions, and buffer against perturbation.

$$\text{Wheat genome: } 3 \text{ subgenomes} \times 7 \text{ chromosomes} \times 2 \text{ (diploid)} = 42 \text{ chromosomes}$$

### Genome size comparison

```python
genomes = {
    'Arabidopsis': 135, 'Rice': 430, 'Maize': 2300, 'Soybean': 1100,
    'Wheat': 17000, 'Barley': 5100, 'Potato': 840, 'Tomato': 950,
    'Cotton': 2500, 'Human': 3200,
}

ploidy = {
    'Arabidopsis': 2, 'Rice': 2, 'Maize': 2, 'Soybean': 4,
    'Wheat': 6, 'Barley': 2, 'Potato': 4, 'Tomato': 2,
    'Cotton': 4, 'Human': 2,
}
# Bar chart of genome sizes (log scale) and ploidy levels
```

### Transposable element content

```python
te_content = {
    'Arabidopsis': 14, 'Rice': 35, 'Sorghum': 62, 'Maize': 85,
    'Wheat': 80, 'Barley': 76, 'Cotton': 67, 'Human': 45,
}
# Stacked bar: TE% vs Genes+Other%
```

### Gene family expansion through WGD

```python
# Ancestral (30k genes) -> WGD (60k) -> Fractionation (39k) -> Tandem dup (41k)
# Plot: duplicate divergence over time (sequence identity vs neofunctionalization)
```

---

## Section 2: Crop Domestication Genetics

Domestication transformed wild plants into crops through intense artificial selection. Genetic signatures include:

- **Selective sweeps**: Reduced diversity near selected genes
- **Bottleneck**: Loss of diversity during domestication
- **Linkage drag**: Unwanted genes hitchhiking with selected alleles

Key domestication genes:
- **tb1** (maize): branching architecture (teosinte -> maize)
- **Sh1** (rice): shattering (seeds stay on plant)
- **Q** (wheat): free-threshing grain

Reference [[Fitness Landscapes]] -- domestication navigates the fitness landscape under human-defined objectives rather than natural selection.

### Domestication bottleneck simulation

```python
# Wild population: uniform allele frequencies (high diversity)
# Bottleneck: binomial sampling from 20 plants
# Modern elite: another bottleneck from 50 plants
# Result: progressive loss of expected heterozygosity (He)
```

### Selective sweep signature

```python
# Diversity across chromosome: uniform 0.3-0.5 in wild
# Around selected gene: exponential reduction
# Plot: diversity valley centered on domestication gene
```

---

## Section 3: Agricultural GWAS

GWAS in crops identifies genomic regions associated with agronomic traits: yield, drought tolerance, disease resistance, grain quality. Unlike human GWAS, plant GWAS can leverage controlled crosses, replicated field trials, and known pedigrees.

Reference [[Variant-Phenotype Mapping]] and [[Genotype-to-Phenotype Hub]] -- the fundamental challenge of mapping genotype to phenotype is the same across species.

### Simulate crop GWAS (yield trait)

```python
# 300 breeding lines, 3000 SNP markers
# 10 QTLs (3 major + 7 minor) affecting yield
# Heritability computed from genetic vs total variance
```

### Manhattan plot and QTL detection

```python
# Single-marker linear regression for each SNP
# Manhattan plot with chromosome coloring
# QTL effect size comparison (detected vs missed)
```

### Genomic prediction (GBLUP-like)

```python
# Ridge regression on all markers simultaneously
# Cross-validated r2
# Prediction accuracy vs training population size
```

---

## Section 4: Genotype x Environment Interaction (GxE)

Genotype x Environment (GxE) interaction means a variety's performance depends on where it is grown. A drought-tolerant line may excel in dry environments but underperform in irrigated conditions.

Reference [[Context Conditionality]] -- f(genotype, environment) -> phenotype. The same genome produces different outcomes in different contexts.

$$Y_{ijk} = \mu + G_i + E_j + (GE)_{ij} + \epsilon_{ijk}$$

### GxE reaction norms

```python
# 8 varieties x 5 environments (Drought, Low N, Standard, Irrigated, Optimal)
# Variety 0: drought specialist (high GxE in dry)
# Variety 3: irrigated specialist (high GxE in wet)
# Reaction norms show crossing lines = GxE
```

### Finlay-Wilkinson stability analysis

```python
# Regression of variety yield on environment mean
# Slope < 1: stable performer
# Slope > 1: responsive to good conditions
# Tradeoff visualization: stability vs responsiveness
```

---

## Section 5: Crop Diversity and Conservation Genetics

Modern breeding progressively narrows the genetic base of crops. Each cycle of selection fixes alleles and removes variation. This "genetic erosion" makes crops vulnerable to new diseases and climate shifts.

Reference [[Robustness and Evolvability]] -- genetic diversity is the raw material for future adaptation.

Reference [[Evolutionary Tinkering]] -- evolution works with existing variation. No variation = no tinkering = no adaptation.

### Diversity across gene pools

```python
# Wild relatives: high diversity (uniform allele frequencies)
# Landraces: moderate diversity
# Elite breeding: reduced diversity
# Released varieties: narrow diversity
# Allele frequency spectra and He comparison
```

### Genetic erosion timeline

```python
# 20 breeding cycles with 5% diversity loss per cycle
# Occasional wild germplasm introduction events restore some diversity
# Critical diversity threshold visualization
```

---

## Summary

| Concept | What you built | Why it matters |
|---------|---------------|----------------|
| Polyploidy | Genome size comparison | Plants break diploid rules |
| TE content | Genome composition | Most plant DNA is mobile elements |
| Gene duplication | WGD + fractionation model | [[Degeneracy in Biological Systems]] |
| Domestication | Bottleneck + sweep simulation | How wild plants became crops |
| Crop GWAS | Yield association mapping | Find genes for breeding |
| Genomic prediction | Ridge regression on markers | Modern breeding tool (GS) |
| GxE interaction | Reaction norms + stability | [[Context Conditionality]] in agriculture |
| Conservation | Diversity erosion | Wild relatives = future food security |

**Connections to conceptual framework:**
- [[Degeneracy in Biological Systems]]: Polyploidy creates redundancy for evolutionary exploration
- [[Fitness Landscapes]]: Domestication navigates landscapes under human objectives
- [[Variant-Phenotype Mapping]]: Crop GWAS maps genotype to yield
- [[Genotype-to-Phenotype Hub]]: The central challenge across all species
- [[Context Conditionality]]: GxE interaction -- same genome, different environments, different yields
- [[Robustness and Evolvability]]: Genetic diversity enables future adaptation
- [[Evolutionary Tinkering]]: Evolution works with existing variation
- [[Plant-Animal Divergence]]: Why plant genomes are so different

**The complete series:**
- [[01_Sequence_Analysis_Fundamentals]] -- Biopython, the Central Dogma
- [[02_Genomic_Variant_Analysis]] -- Population genetics, GWAS
- [[03_Single_Cell_Transcriptomics]] -- scanpy, cell type discovery
- [[04_Protein_Structure_Drug_Discovery]] -- Structure and drug design
- [[05_Bulk_RNAseq_Differential_Expression]] -- Differential expression analysis
- [[06_Clinical_Biomedical_Informatics]] -- Clinical data and survival analysis
- [[07_Biomedical_Image_Analysis]] -- Pathology and radiology
- [[08_Plant_Biology_Agricultural_Genomics]] -- Crops and food security (this notebook)
