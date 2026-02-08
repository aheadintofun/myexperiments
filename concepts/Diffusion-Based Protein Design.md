# Diffusion-Based Protein Design

## Definition
Generative modeling approach that designs novel protein backbone geometries by reversing a noise-diffusion process. Unlike predictive models (AlphaFold), diffusion models **hallucinate** new protein structures conditioned on functional constraints (e.g., "binds to this target", "forms this shape").

## Computational Structure
The diffusion process operates in SE(3) space (3D rotations and translations):

$$\text{Random Noise} \xrightarrow{\text{learned denoising}} \text{Protein Backbone}$$

Conditioned generation:
$$\text{Random Noise} + \text{Target Constraint} \xrightarrow{\text{guided diffusion}} \text{Binder Backbone}$$

## Core Algorithm (RFdiffusion, 2023)
1. **Training**: Learn to denoise corrupted protein structures from PDB
2. **Inference**: Start from noise, iteratively denoise while enforcing constraints
3. **Constraints**:
   - "Design binder to protein X" (hotspot residues specified)
   - "Design symmetric oligomer" (C3, D4 symmetry)
   - "Design fold topology" (all-alpha, beta-barrel)
4. **Output**: Backbone Cα coordinates (no sequence yet—use [[Inverse Folding]] for that)

## Design Workflow
The modern generative protein pipeline (2023-2026):

1. **RFdiffusion**: Generate candidate backbone geometries
2. **ProteinMPNN**: Design sequences for each backbone
3. **AlphaFold**: Validate that sequences fold to intended structure
4. **Filters**: Keep only designs where predicted structure matches designed backbone (RMSD < 2Å)
5. **Experimental**: Synthesize top candidates, measure binding affinity

## Breakthrough Applications

### De Novo Binders
Design proteins that bind therapeutic targets (insulin, PD-1, SARS-CoV-2 RBD):
- No homology to natural proteins
- Success rate: ~10-20% of designs show binding in wet lab
- Orders of magnitude faster than phage display

### Enzyme Active Sites
Design protein scaffolds around catalytic residues:
- Specify geometry of catalytic triad
- Diffusion model builds stable scaffold around it
- Applications: custom enzymes for industrial chemistry

### Symmetric Assemblies
Design protein cages, nanoparticles, filaments:
- Vaccine scaffolds (multivalent antigen display)
- Targeted drug delivery vehicles
- Biomaterials with programmable mechanics

## Key Insight
Diffusion models explore **regions of protein space inaccessible to evolution**. Natural proteins evolved under constraint (must be expressible, stable in cells, evolutionarily accessible). Designed proteins only need to satisfy functional constraints—opening vast new regions of structure space.

## Computational Requirements
**Expensive** compared to structure prediction:
- CUDA-dependent (SE(3) transformer kernels)
- GPU required (NVIDIA T4 minimum, A100 preferred)
- 10-100x slower than AlphaFold inference
- Google Colab is standard platform (Mac M4 not supported)

## Related Concepts
- [[Protein Structure Prediction]] - Validates designed structures
- [[Inverse Folding]] - Sequences designed backbones
- [[Protein Language Models]] - Alternative generative approach via sequence space
- [[Molecular Docking]] - Validates binding interfaces
- [[Information Compression in Biology]] - Generative models learn compressed latent spaces

## Tags
#protein-design #diffusion-models #generative-ai #rfdiffusion #de-novo-design #binder-design #structural-biology
