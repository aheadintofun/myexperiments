# Turing Pattern Formation

## Definition
Spontaneous emergence of spatial patterns from initially homogeneous conditions via reaction-diffusion dynamics. Two interacting chemical species—an activator and inhibitor with different diffusion rates—create stable periodic patterns (stripes, spots, labyrinths).

## Mathematical Mechanism
Alan Turing (1952) showed that diffusion, typically stabilizing, can **destabilize** uniform states when coupled to chemical reactions.

### Reaction-Diffusion Equations
$$\frac{\partial u}{\partial t} = D_u \nabla^2 u + f(u, v)$$
$$\frac{\partial v}{\partial t} = D_v \nabla^2 v + g(u, v)$$

Where:
- $u$: Activator concentration (promotes own production)
- $v$: Inhibitor concentration (suppresses activator)
- $D_u, D_v$: Diffusion coefficients
- $f, g$: Reaction kinetics

### Turing Instability Condition
Pattern formation requires:
1. Inhibitor diffuses faster than activator: $D_v > D_u$
2. Local activation, lateral inhibition dynamics
3. System size larger than critical wavelength

Result: Uniform state unstable to perturbations at specific wavelengths. System evolves to spatial pattern with characteristic length scale:
$$\lambda \sim \sqrt{\frac{D_v}{k}}$$

Where $k$ is reaction rate constant.

## Pattern Types

### Spots
Localized activator peaks (e.g., pigment spots on fish, leopard).

### Stripes
Parallel bands (e.g., zebra stripes, digit formation).

### Labyrinths
Maze-like connected structures (e.g., coral patterns, brain convolutions).

Pattern type depends on:
- Ratio $D_v / D_u$
- Reaction kinetics $f, g$
- Boundary conditions
- System geometry

## Biological Examples

### Developmental Biology
**Digit patterning**: Sonic hedgehog (Shh) as activator, Bmp as inhibitor.
- Diffusion creates periodic pre-pattern
- Pre-pattern specifies digit positions in limb bud

**Hair follicle spacing**: WNT (activator), DKK (inhibitor).
- Ensures even distribution of follicles
- Disruption causes patchy hair loss

**Left-right asymmetry**: Nodal (activator), Lefty (inhibitor).
- Breaks bilateral symmetry in early embryo
- Specifies organ laterality (heart on left)

### Morphogenesis
**Hydra regeneration**: Head activator, head inhibitor.
- Amputated piece re-establishes head-foot axis
- Turing mechanism creates new organizing center

**Feather bud patterns**: Avian skin epithelia.
- Reaction-diffusion pre-pattern
- Buds form at pattern peaks

### Pigmentation
**Animal coat patterns**: Melanocyte activator, inhibitor.
- Stripes (zebra, tiger)
- Spots (cheetah, giraffe)
- Irregular (tortoiseshell cat—temperature-dependent)

## Extensions and Variants

### Multiple Morphogens
More than two species create richer patterns:
- Nested domains
- Hierarchical segmentation (somitogenesis)

### Anisotropic Diffusion
Directional bias in diffusion:
- Elongated patterns (parallel stripes vs hexagons)
- Tissue anisotropy guides pattern orientation

### Discrete Cellular Automata
Turing patterns on lattices:
- Cellular automaton rules approximate reaction-diffusion
- Discrete space, discrete time, discrete states

See [[Cellular Automata Framework]].

## Key Insight
Local interactions (reaction kinetics) + global coupling (diffusion) → spontaneous pattern. No external template required. The wavelength is **intrinsic** to system parameters, not imposed by boundary conditions.

This is **symmetry breaking**: homogeneous state (symmetric) destabilizes to patterned state (asymmetric).

## Related Concepts
- [[Symmetry Breaking in Biological Systems]] - Turing patterns as symmetry-breaking mechanism
- [[Cellular Automata Framework]] - Discrete analog on lattice
- [[Morphogenesis]] - Developmental pattern formation
- [[Lattice and Spatial Modeling Hub]] - Spatial substrate for patterns
- [[Critical Phenomena]] - Pattern wavelength diverges at critical point

## Tags
#turing-patterns #reaction-diffusion #pattern-formation #morphogenesis #symmetry-breaking #developmental-biology #spatial-structure
