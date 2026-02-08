# Inverse Folding

## Definition
The computational problem of designing amino acid sequences that fold into a specified three-dimensional structure. This reverses the traditional protein folding problem: given a target backbone geometry, find sequences that stabilize it.

## Computational Structure
The inverse mapping:
$$\text{3D Backbone} \xrightarrow{\text{sequence design}} \text{Amino Acid Sequence}$$

This is a **one-to-many** problem—many sequences can fold to the same structure. The goal is to find sequences that:
- Fold to the target structure (**foldability**)
- Are thermodynamically stable (**low free energy**)
- Are experimentally expressible (**solubility, avoid aggregation**)

## Core Algorithm (ProteinMPNN, 2022)
Message-passing neural network trained on PDB structures:
1. Input: Backbone Cα coordinates + target chain specification
2. Encoder: Graph neural network over residue-residue distances
3. Decoder: Autoregressive sequence generation with temperature control
4. Output: 10-100 candidate sequences ranked by model confidence

## Applications

### Stability Enhancement
Take natural protein → predict structure → redesign sequence for higher melting temperature
- Used for therapeutic antibodies and industrial enzymes
- Common improvement: +10-20°C thermostability

### De Novo Binder Design
Workflow with RFdiffusion:
1. RFdiffusion generates backbone binding to target
2. ProteinMPNN designs sequences for that backbone
3. AlphaFold validates that sequences fold as intended
4. Experimental synthesis and binding assay

### Computational Protein Evolution
Iterative refinement:
1. Design sequence for backbone
2. Predict structure of designed sequence
3. Optimize backbone based on predicted structure
4. Repeat until convergence

## Key Insight
Inverse folding enables **programmable protein design**. Instead of evolving proteins through random mutagenesis, we can directly specify structural constraints and generate sequences computationally. This is **rational design** replacing directed evolution.

## Hardware Requirements
Extremely lightweight compared to structure prediction:
- Runs on CPU in seconds (ProteinMPNN)
- No GPU required
- 1000x faster than AlphaFold inference
- Native Mac M4 support

## Related Concepts
- [[Protein Structure Prediction]] - The forward problem
- [[Diffusion-Based Protein Design]] - Generates backbone geometries for inverse folding
- [[Protein Language Models]] - Alternative sequence design via evolutionary likelihood
- [[Variant-Phenotype Mapping]] - Designed sequences must map to intended function
- [[Degeneracy in Biological Systems]] - Many sequences map to same fold

## Tags
#protein-design #inverse-folding #rational-design #proteinmpnn #sequence-design #structural-biology
