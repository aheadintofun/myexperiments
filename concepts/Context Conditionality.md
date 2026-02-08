# Context Conditionality

## Definition
Every biological mapping is **conditional on context**. The same genotype produces different phenotypes, the same drug has different effects, the same crop trait varies by environment. The real object is not a function but a **conditional distribution**.

## Mathematical Form
Instead of deterministic mapping:
$$f(\text{genotype}) \rightarrow \text{phenotype}$$

Reality is:
$$P(\text{phenotype} \mid \text{genotype}, \mathbf{c})$$

Where $\mathbf{c}$ is a high-dimensional context vector.

## Context Vector Components
- **Genetic background**: Modifier genes, epistatic interactions
- **Developmental stage**: Embryonic vs adult, cell cycle phase
- **Spatial location**: Tissue type, microenvironment niche
- **Environmental factors**: Temperature, nutrients, toxins, pathogens
- **Temporal dynamics**: Circadian phase, seasonal variation
- **Prior history**: Developmental trajectory, exposure history
- **Stochastic noise**: Intrinsic fluctuations, measurement error

## Examples of Context Dependence

### Genetic Penetrance
Same pathogenic variant:
- High penetrance in permissive genetic background
- Low penetrance with modifier alleles
- Incomplete penetrance from stochastic factors

### Drug Response
Same therapeutic:
- Effective in treatment-naive tumors
- Ineffective after prior resistance
- Variable across microenvironment niches (hypoxic vs normoxic)

### Crop Traits
Same cultivar:
- High yield in optimal soil/climate
- Poor yield under drought stress
- Disease-resistant in one pathogen strain, susceptible in another

### Immune Recognition
Same TCR sequence:
- Autoreactive in one HLA context
- Pathogen-specific in another HLA context
- Non-functional in MHC-mismatched individual

## Computational Challenge
The context vector is:
- **High-dimensional**: Many interacting factors
- **Partially observable**: Can't measure all components
- **Dynamic**: Changes over time
- **Hierarchical**: Context at molecular, cellular, organismal levels

Standard regression approaches fail. Need:
- Hierarchical Bayesian models
- Latent variable models
- Context-aware neural networks
- Causal inference methods

## Related Concepts
- [[Variant-Phenotype Mapping]] - Conditioned on context
- [[Microenvironment Context]] - Spatial component of context
- [[Degeneracy in Biological Systems]] - Same function in different contexts
- [[Hierarchical Composition]] - Context defined at each hierarchical level
- [[Multi-Scale Lattice]] - Context as surrounding lattice configuration

## Tags
#context-dependency #conditional-probability #epistasis #gene-environment-interaction #penetrance #personalized-medicine
