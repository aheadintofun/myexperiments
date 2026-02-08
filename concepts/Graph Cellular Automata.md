# Graph Cellular Automata

## Definition
A generalization of cellular automata where the regular lattice is replaced by an arbitrary graph. Each node has a state, and update rules depend on the states of connected neighbors. The graph topology encodes the interaction structure.

## Unifying Framework
Social networks, protein interaction networks, and ecological food webs become the **same computational object** with different topologies and update rules:
- **Nodes**: Agents, proteins, species
- **Edges**: Interactions, bonds, predation relationships
- **Update rules**: Dynamics specific to the domain
- **Topology**: The connectivity pattern

## Advantages Over Regular Lattices
- Models realistic network topologies (scale-free, small-world, modular)
- Captures long-range interactions (not just nearest neighbors)
- Represents heterogeneous connectivity naturally
- No artificial periodic boundary conditions

## Examples

### Social Networks
- Nodes: Individuals
- Edges: Social connections
- State: Opinion, health status, information
- Dynamics: Influence, contagion, diffusion

### Protein Networks
- Nodes: Proteins or genes
- Edges: Physical interactions or regulatory relationships
- State: Expression level, modification state
- Dynamics: Signaling cascades, feedback loops

### Ecological Networks
- Nodes: Species populations
- Edges: Predation, competition, mutualism
- State: Population size
- Dynamics: Lotka-Volterra, trophic cascades

## Related Concepts
- [[Cellular Automata Framework]] - Regular lattice version
- [[Heterogeneous Lattice]] - Irregular spatial structure
- [[Network Topology]] - Graph structure properties
- [[Update Rule as Fundamental Unit]] - Dynamics on graph edges

## Tags
#graph-theory #cellular-automata #network #topology #generalization #complex-systems
