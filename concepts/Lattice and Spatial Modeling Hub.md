# Lattice and Spatial Modeling Hub

## Conceptual Overview

Biological systems are fundamentally **spatial**—cells arranged in tissues, organisms distributed across landscapes, neurons wired in networks. The lattice framework provides a universal computational substrate for modeling these spatial structures and their dynamics.

The unifying thread: **local interactions produce global patterns**. Each lattice site represents an agent (cell, organism, person) whose state evolves according to rules that depend only on its local neighborhood. Emergent complexity arises not from complicated individual behavior, but from simple rules iterated across space and time.

## Core Framework

```
                  LATTICE MODELING STACK

    ┌─────────────────────────────────────────┐
    │  Global Patterns (emergent)             │
    │  • Morphogenesis                        │
    │  • Tumor invasion fronts                │
    │  • Epidemic waves                       │
    └─────────────────────────────────────────┘
                      ▲
                      │ Emergence
                      │
    ┌─────────────────────────────────────────┐
    │  Local Update Rules                     │
    │  f(neighborhood) → next_state           │
    └─────────────────────────────────────────┘
                      ▲
                      │ Depends on
                      │
    ┌─────────────────────────────────────────┐
    │  Lattice Topology                       │
    │  • Regular grids                        │
    │  • Heterogeneous connectivity           │
    │  • Arbitrary graphs                     │
    └─────────────────────────────────────────┘
```

## Conceptual Ladder

### Foundation: Regular Lattices
**[[Cellular Automata Framework]]** - The canonical structure: grid topology, state vectors at each site, synchronous updates from local rules. This is the Conway's Game of Life paradigm.

### Generalization 1: Non-Uniform Topology
**[[Heterogeneous Lattice]]** - Not all sites need the same connectivity. Tissue microarchitecture has blood vessels, stromal cells, immune cells with different neighbor counts and interaction types.

### Generalization 2: Hierarchical Nesting
**[[Multi-Scale Lattice]]** - Each lattice site is itself a lattice. Protein networks inside cells, cells inside tissues, tissues inside organisms, organisms inside populations. Renormalization appears naturally.

### Generalization 3: Arbitrary Networks
**[[Graph Cellular Automata]]** - Replace regular grid with arbitrary graph. Social networks, protein interaction networks, ecological food webs—all become special cases of the lattice framework.

### Primitive: The Update Rule
**[[Update Rule as Fundamental Unit]]** - The algebraic atom of lattice dynamics. Each boundary interaction is a function mapping neighborhood state to next state. Composition of update rules generates system evolution.

## Cross-Scale Phenomena

### Spatial Context Matters
**[[Microenvironment Context]]** - A cell's phenotype depends on its neighbors. T cell activation requires the right antigen-presenting cell in the right tissue context. Tumor cells behave differently at invasion front vs core.

### Communication Across Scales
**[[Cross-Boundary Signaling]]** - Information flows between hierarchical levels. Hormones carry organism-level state to tissue-level decisions. Intracellular calcium oscillations coordinate multicellular waves.

## Mathematical Foundations

### State Space Formulation
Each lattice configuration is a point in state space:
$$\mathbf{X}(t) = \{x_1(t), x_2(t), \ldots, x_N(t)\}$$

Where $x_i(t)$ is the state vector at site $i$ at time $t$.

### Update Operator
The dynamics are a map $\mathcal{F}$ on state space:
$$\mathbf{X}(t+1) = \mathcal{F}(\mathbf{X}(t))$$

Decomposing into local rules:
$$x_i(t+1) = f_i(\{x_j : j \in \mathcal{N}(i)\})$$

Where $\mathcal{N}(i)$ is the neighborhood of site $i$.

### Coarse-Graining
Moving from fine-grained lattice to coarse-grained requires finding **effective update rules**:
$$\tilde{f}(\text{coarse state}) \approx \text{aggregation}(f(\text{fine state}))$$

This is the renormalization problem. See [[Renormalization in Biological Systems]].

## Applications Across Biology

| Domain | Lattice Sites | State Vector | Update Rule | Emergent Pattern |
|--------|---------------|--------------|-------------|------------------|
| **Developmental biology** | Cells in embryo | Gene expression | Morphogen gradients + cell-cell contact | Tissue boundaries, organ shape |
| **Tumor growth** | Cancer cells + stroma | Proliferation, hypoxia, mutations | Contact inhibition, resource competition | Invasion fronts, necrotic cores |
| **Epidemiology** | Individuals in population | Susceptible/Infected/Recovered | Contact-mediated transmission | Epidemic waves, herd immunity |
| **Ecology** | Organisms in habitat | Species, age, resources | Predation, competition, reproduction | Population cycles, spatial segregation |
| **Neuroscience** | Neurons in network | Firing rate, synaptic weights | Spike integration, plasticity | Synchronization, traveling waves |

## Key Insights

1. **Topology encodes constraints**: Regular grids impose geometric order. Random graphs enable small-world connectivity. Hierarchical lattices create scale separation.

2. **Local rules, global consequences**: No central controller. Patterns emerge from distributed interactions.

3. **Same formalism, different scales**: The cellular automaton framework applies from proteins to ecosystems—only the physical interpretation changes.

4. **Renormalization is inevitable**: Multiscale systems require coarse-graining. Effective theories at each scale.

## Design Patterns

### Pattern 1: Reaction-Diffusion
Lattice sites exchange particles/signals with neighbors:
- **Reaction**: Local transformation within site
- **Diffusion**: Exchange between sites
- **Result**: Turing patterns, morphogen gradients

See [[Turing Pattern Formation]].

### Pattern 2: Percolation
Sites randomly activate. Global connectivity phase transition when activation probability crosses threshold.
- **Application**: Epidemic spread, habitat fragmentation
- **Critical exponents**: Universal behavior near threshold

See [[Critical Phenomena]].

### Pattern 3: Voting Models
Site state influenced by neighbor majority:
- **Application**: Opinion dynamics, immune cell polarization
- **Symmetry breaking**: Homogeneous population → clustered domains

See [[Symmetry Breaking in Biological Systems]].

## Related Hubs
- [[Biological Dynamics Hub]] - Temporal evolution on lattices
- [[Genotype-to-Phenotype Hub]] - Lattice as substrate for variant effects
- [[Computational Biology Tools Hub]] - Implementation frameworks

## Tags
#hub #lattice-modeling #cellular-automata #spatial-structure #emergence #multi-scale #topology #update-rules
