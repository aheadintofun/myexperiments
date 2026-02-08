# Protein Structure Prediction

## Definition
The computational problem of determining the three-dimensional atomic coordinates of a protein given only its amino acid sequence. Solving this problem—known as the "protein folding problem"—enables understanding of protein function, drug binding, and disease mechanisms without experimental crystallography.

## Computational Structure
The mapping follows:
$$\text{Sequence} \xrightarrow{\text{physics + evolution}} \text{3D Structure}$$

Modern approaches use:
- **Physics-based**: Energy minimization over conformational space
- **Knowledge-based**: Evolutionary constraints from multiple sequence alignments (MSA)
- **Deep learning**: Neural networks trained on PDB structures (AlphaFold 2/3, Boltz-1, Chai-1)

## Scale Hierarchy
Structure prediction operates at multiple levels:

### Single-Chain Proteins
- Input: FASTA sequence (100-1000 residues)
- Output: PDB coordinates with per-residue confidence scores
- AlphaFold 2, ESMFold (MSA-free)

### Multi-Chain Complexes
- Input: Multiple sequences (protein-protein, protein-nucleic acid)
- Output: Interface geometry and interaction residues
- AlphaFold 3, Boltz-1, Chai-1

### Protein-Ligand Binding
- Input: Protein sequence + small molecule SMILES
- Output: Binding pose and affinity prediction
- AlphaFold 3, Chai-1 (combines folding + docking)

## Breakthrough Shift (2021-2026)
**Before 2021**: Homology modeling limited to sequences with known templates, physics-based methods computationally expensive and often inaccurate.

**After AlphaFold 2**: Deep learning models achieve experimental accuracy (RMSD < 2Å for >90% of domains). The bottleneck shifts from "Can we predict structure?" to "What do we do with millions of predicted structures?"

## Key Insight
Structure prediction is no longer a specialized computational task—it is a **solved lookup problem**. The AlphaFold Protein Structure Database contains >200 million predicted structures. The frontier has moved to **interaction prediction** and **dynamics**.

## Related Concepts
- [[Variant-Phenotype Mapping]] - Structure mediates sequence-to-function mapping
- [[Information Compression in Biology]] - Embeddings capture structural similarity
- [[Molecular Docking]] - Predicting binding without folding
- [[Inverse Folding]] - Designing sequences for target structures
- [[Protein Language Models]] - Evolutionary patterns learned from sequences

## Tags
#structure-prediction #alphafold #protein-folding #deep-learning #structural-biology #computational-biology
