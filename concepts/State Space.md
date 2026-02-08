# State Space

## Definition
The set of all possible configurations a biological system can occupy. Each point in state space represents a complete specification of the system at one instant. Trajectories through state space describe how systems evolve over time.

## Mathematical Structure
For a system with $N$ components, each with $M$-dimensional state:
$$\mathcal{S} = \mathbb{R}^{N \times M}$$

A state vector at time $t$:
$$\mathbf{x}(t) = (x_1(t), x_2(t), \ldots, x_N(t)) \in \mathcal{S}$$

## Biological Examples

### Single Cell
State = gene expression levels (20,000 genes):
$$\mathbf{x}_\text{cell} \in \mathbb{R}^{20000}$$

### Tissue Lattice
State = collection of cell states on spatial grid:
$$\mathbf{x}_\text{tissue} = \{x_i : i \in \text{lattice sites}\}$$

### Population
State = genotype frequencies in population:
$$\mathbf{x}_\text{pop} = (f_1, f_2, \ldots, f_K)$$
Where $\sum f_i = 1$ (frequencies sum to 1).

## Dynamics as Trajectories
Evolution governed by differential equations:
$$\frac{d\mathbf{x}}{dt} = \mathbf{F}(\mathbf{x}, t)$$

Trajectories are paths $\mathbf{x}(t)$ through state space.

## Attractors and Stability
**Attractor**: Subset of state space trajectories converge to.

Examples:
- **Fixed point**: Stable cell type, homeostatic equilibrium
- **Limit cycle**: Circadian rhythm, cell cycle oscillations
- **Strange attractor**: Chaotic dynamics (some epidemic models)

## Key Insight
State space formalism unifies disparate biological phenomena. Developmental trajectories, drug responses, evolutionary dynamics—all are paths through state space. Understanding biology = understanding the geometry and topology of these spaces.

## Related Concepts
- [[Trajectory and Branching Fate]] - Paths through state space
- [[Fitness Landscapes]] - Fitness as function on genotype state space
- [[Perturbation-Response-Adaptation]] - State space before/after perturbation
- [[Cellular Automata Framework]] - Discrete state space on lattice
- [[Transfer Functions]] - Mapping perturbations to state changes

## Tags
#state-space #dynamical-systems #trajectories #attractors #mathematical-foundations
