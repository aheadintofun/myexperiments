# Molecular Docking

## Definition
The computational problem of predicting the binding geometry and affinity of a small molecule (ligand) to a protein target. Critical for drug discovery—enables virtual screening of millions of compounds before experimental synthesis.

## Computational Structure
The optimization problem:
$$\underset{\text{pose}}{\arg\min} \; E(\text{protein}, \text{ligand}, \text{pose})$$

Where:
- **Pose** = 3D position and orientation of ligand in binding pocket
- **E** = Scoring function (physics-based or learned)
- **Search space** = 6 degrees of freedom (3 translation, 3 rotation) + internal torsions

## Method Evolution

### Classical Physics-Based (2000-2020)
- AutoDock Vina, Glide, GOLD
- Energy functions: van der Waals, electrostatics, desolvation
- Search: Genetic algorithms, Monte Carlo, gradient descent
- **Limitation**: Rigid or semi-flexible binding sites, poor ranking of poses

### Machine Learning Docking (2022-2026)
- DiffDock (2022): Diffusion over SE(3) pose space
- Chai-1 (2024): Joint folding + docking in single model
- AlphaFold 3 (2024): Predicts protein-ligand complexes end-to-end

**Breakthrough**: No longer need known structure—models fold protein and dock ligand simultaneously.

## Docking Hierarchy

### Rigid Docking
- Protein structure fixed
- Ligand placed in known binding pocket
- Fast (seconds per compound)
- Use: Virtual screening of drug libraries

### Flexible Docking
- Protein side chains move
- Ligand internal bonds rotate
- Slow (minutes per compound)
- Use: Lead optimization

### Blind Docking
- No prior knowledge of binding site
- Search entire protein surface
- Very slow (hours per compound)
- DiffDock enables blind docking at flexible docking speed

### Co-Folding + Docking
- Protein structure predicted from sequence
- Ligand docked to predicted structure in single inference
- Chai-1, AlphaFold 3
- Use: Docking to proteins without experimental structures

## Key Insight
The 2024-2026 revolution: **docking is no longer separate from folding**. Modern models predict protein structure and ligand binding pose in a unified framework. This enables:
- Drug discovery for proteins without crystal structures
- Predicting effects of mutations on drug binding
- Designing ligands for computationally designed proteins

## Validation Challenge
**The problem**: Docking models can generate plausible-looking poses that are biophysically impossible.

**Solutions**:
- Validate top hits with molecular dynamics (MD) simulations
- Experimental binding assays (SPR, ITC) for top 10-100 compounds
- Use consensus docking (multiple methods must agree)

## Hardware Requirements

### Classical Docking
- CPU-only, fast
- Can run on laptop
- Parallelize across compound library

### ML-Based Docking
- **DiffDock**: GPU preferred, Colab-friendly
- **Chai-1**: Mac M4 slow but possible, Colab recommended
- **AlphaFold 3**: Server-only (computational cost prohibitive for local)

## Related Concepts
- [[Protein Structure Prediction]] - Provides receptor structures for docking
- [[Diffusion-Based Protein Design]] - Docking validates designed binders
- [[Variant-Phenotype Mapping]] - Mutations affect binding affinity
- [[Information Compression in Biology]] - Binding pockets are compressed representations of ligand space

## Tags
#molecular-docking #drug-discovery #protein-ligand-binding #diffdock #chai #virtual-screening #structure-based-drug-design
