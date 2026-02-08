# Symmetry Breaking in Lattice Systems

## Definition
Spontaneous emergence of asymmetric patterns on initially uniform lattices with symmetric update rules. A specific instance of [[Symmetry Breaking in Biological Systems]] implemented on [[Cellular Automata Framework]].

## Core Mechanism
1. **Uniform initial state**: All lattice sites identical
2. **Symmetric local rules**: Update rules same everywhere, no inherent asymmetry
3. **Small perturbation**: Random fluctuation or deliberate seed
4. **Positive feedback**: Perturbation amplified through local interactions
5. **Asymmetric stable state**: System settles into patterned configuration

**Key insight**: **Asymmetry emerges from symmetric rules**—pattern is not encoded in rules, it arises spontaneously.

## Examples on Lattices

### Ising Model
- **Lattice**: 2D grid, spins $\sigma_i = \pm 1$
- **Hamiltonian**: $H = -J \sum_{\langle ij \rangle} \sigma_i \sigma_j$ (favor aligned neighbors)
- **High temperature**: Random spins (symmetric)
- **Low temperature**: Ferromagnetic order (all spins aligned—symmetry broken)
- **Critical point**: $T_c$ where transition occurs

### Majority Rule Dynamics
- **Lattice**: Network, nodes with binary states
- **Update**: Node adopts majority state of neighbors
- **Outcome**: Lattice segregates into domains (symmetry broken)

### Schelling Segregation Model
- **Lattice**: 2D grid, agents of two types
- **Rule**: Agent moves if <30% neighbors are same type
- **Outcome**: Homogeneous clusters form (spatial segregation)

### Turing Patterns on Lattices
See [[Turing Pattern Formation]]:
- **Lattice**: Spatial grid for reaction-diffusion
- **Rules**: Activator-inhibitor dynamics (local production/diffusion)
- **Outcome**: Spots, stripes, labyrinthine patterns

### Percolation
- **Lattice**: Random graph, edges added with probability $p$
- **Below threshold ($p < p_c$)**: Only small clusters
- **Above threshold ($p > p_c$)**: Giant connected component emerges (symmetry breaking)

## Why Lattices Facilitate Symmetry Breaking

### Local Interactions
See [[Local Interaction]]:
- Lattice structure defines neighborhoods
- Each site interacts only with neighbors
- **Result**: Global pattern emerges without global coordination

### Emergent Global Pattern
See [[Emergent Global Pattern]]:
- No blueprint for pattern
- [[Update Rule as Fundamental Unit]]: Simple local rules
- **Iteration**: Pattern arises from repeated application

### Spatial Structure
Lattice provides spatial scaffolding:
- Diffusion, nearest-neighbor coupling naturally implemented
- Enables reaction-diffusion mechanisms (Turing)
- Supports domain formation, interfaces

## Phase Transitions
Symmetry breaking often occurs at critical points (see [[Critical Phenomena]]):
- **Order parameter**: Measures degree of asymmetry (magnetization, cluster size)
- **Critical temperature/coupling**: $T_c$, $p_c$ where transition occurs
- **Universality**: Details of lattice don't matter, critical exponents universal

## Computational Implementation

### Cellular Automata
See [[Cellular Automata Framework]]:
- Discrete lattice sites, discrete states
- Synchronous or asynchronous update
- **Examples**: Conway's Game of Life, forest fire model

### Lattice Gas / Lattice Boltzmann
- Lattice-based fluid dynamics
- Particles hop between sites
- Emergent hydrodynamics, pattern formation

### Monte Carlo Methods
- Metropolis-Hastings, Gibbs sampling on lattice
- Simulate equilibrium distributions
- Study phase transitions (Ising model)

## Biological Applications

### Morphogenesis
[[Morphogenesis]]: Tissue patterning as lattice symmetry breaking:
- Cells as lattice sites
- Signaling molecules diffuse between sites
- Turing-like patterns → somites, digits, skin patterns

### Social Dynamics
- **Schelling model**: Residential segregation
- **Opinion dynamics**: Consensus formation, polarization
- Lattice of agents with local interaction rules

### Ecosystem Patterning
- **Vegetation banding**: Arid landscapes, self-organized stripes
- **Predator-prey waves**: Spatial oscillations on lattice

## Relationship to Continuous Symmetry Breaking
Lattice models are **discrete approximations** of continuous systems:
- Continuous: Reaction-diffusion PDEs
- Discrete: Lattice with diffusion steps
- **Limit**: As lattice spacing → 0, recover continuous equations

## Bifurcation Analysis
Symmetry breaking = **bifurcation** in parameter space:
- **Below critical value**: Symmetric state stable
- **Above critical value**: Symmetric state unstable, asymmetric states stable
- **Bifurcation point**: $\lambda = \lambda_c$ where stability changes

## Related Concepts
- [[Symmetry Breaking in Biological Systems]] - General biological symmetry breaking
- [[Cellular Automata Framework]] - Lattice substrate for dynamics
- [[Local Interaction]] - Mechanism: local rules drive global pattern
- [[Emergent Global Pattern]] - Patterns arise without global coordination
- [[Turing Pattern Formation]] - Reaction-diffusion symmetry breaking
- [[Critical Phenomena]] - Phase transitions and universality
- [[Update Rule as Fundamental Unit]] - Local rules as primitives

#symmetry-breaking #lattice-models #cellular-automata #phase-transitions #pattern-formation #emergence
