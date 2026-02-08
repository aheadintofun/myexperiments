# Network Topology

## Definition
The pattern of connections between nodes in a network—**who is connected to whom**. In biology, topology determines how signals propagate, how robust systems are to damage, and what collective behaviors emerge.

## Core Insight
**Topology is not just wiring—it encodes computational capacity and evolutionary constraints.**

Same nodes, same edge weights, different topology → radically different dynamics.

## Types of Biological Networks

### Molecular Networks
- **Protein-protein interaction networks**: Physical binding partners
- **Gene regulatory networks**: Transcription factors regulating target genes
- **Metabolic networks**: Enzymes catalyzing reactions (substrates/products as edges)
- **Signaling networks**: Cascades of phosphorylation, second messengers

### Cellular Networks
- **Neural networks**: Synaptic connections between neurons
- **Gap junction networks**: Electrical coupling between cells
- **Vascular networks**: Capillary beds, arterial/venous trees

### Organismal Networks
- **Ecological networks**: Food webs, symbiotic relationships, competition
- **Social networks**: Mating networks, dominance hierarchies, cooperation
- **Epidemiological networks**: Contact networks for disease spread

## Network Motifs
Recurring small subgraphs with functional significance:

### Feedforward Loop (FFL)
```
A → B → C
A -------→ C
```
- **Function**: Temporal filtering, delay
- **Example**: Gene regulation (repressor needs time to clear)

### Negative Feedback Loop
```
A → B → C
↑       ↓
←-------
```
- **Function**: Homeostasis, oscillation dampening
- **Example**: Endocrine regulation (hormone suppresses own production)

### Positive Feedback Loop
```
A → B → A
```
- **Function**: Bistability, commitment, memory
- **Example**: Cell cycle checkpoints, differentiation decisions

## Topological Properties

### Degree Distribution
- **Random network**: Poisson distribution
- **Scale-free network**: Power-law $P(k) \sim k^{-\gamma}$ (common in biology)
- **Hub nodes**: High-degree nodes dominating connectivity

### Path Length
- **Average path length**: Mean distance between any two nodes
- **Small-world property**: Short average path despite mostly local connections
- **Biological implication**: Fast signal propagation across organism

### Clustering
- **Clustering coefficient**: Probability that two neighbors of a node are also connected
- **High clustering**: Modular organization, functional units
- **Low clustering**: Broadcast networks, hierarchical signaling

### Modularity
- **Community structure**: Network divides into densely connected subgraphs
- **Biological modules**: Pathways, protein complexes, tissue compartments
- See [[Hierarchical Composition]]

## Topological Robustness

### Attack Tolerance
- **Random node failure**: Scale-free networks robust (most nodes low-degree)
- **Targeted hub removal**: Scale-free networks fragile
- **Biological example**: Knocking out hub genes often lethal

### Degeneracy
Multiple pathways achieve same function (see [[Degeneracy in Biological Systems]]):
- **Redundancy**: Parallel paths increase robustness
- **Bypass routes**: Alternative pathways compensate for damaged nodes
- **Example**: Metabolic networks have high redundancy

## Dynamics on Networks

### Synchronization
- **Coupled oscillators**: Topology determines synchronization threshold
- **Example**: Circadian clocks in suprachiasmatic nucleus, heartbeat pacemakers

### Percolation and Epidemics
- **Percolation threshold**: Minimum edge density for spanning cluster
- **Epidemic threshold**: $R_0 = 1$ depends on degree distribution
- See [[Critical Phenomena]]

### Information Flow
- **Betweenness centrality**: Nodes/edges on many shortest paths control flow
- **Bottlenecks**: High-betweenness nodes are information choke points
- **Example**: Signaling hubs integrate multiple pathways

## Graph Cellular Automata Connection
[[Graph Cellular Automata]] uses arbitrary network topology as substrate:
- Nodes = lattice sites (cells, genes, organisms)
- Edges = interaction structure
- Topology determines update rule neighborhoods
- See [[Update Rule as Fundamental Unit]]

## Evolutionary Perspective

### Network Growth Mechanisms
- **Preferential attachment**: New nodes connect to high-degree nodes → scale-free networks
- **Duplication-divergence**: Gene duplication preserves some edges, adds new ones
- **Horizontal gene transfer**: Adds edges between distant taxa

### Topological Evolution
Network topology itself under selection:
- **Robustness**: Redundant paths
- **Efficiency**: Short paths, low wiring cost
- **Evolvability**: Modularity enables independent variation (see [[Robustness and Evolvability]])

## Computational Tools
- **NetworkX (Python)**: General network analysis
- **iGraph (R/Python)**: Fast graph algorithms
- **Cytoscape**: Visualization, especially biological networks
- **SCENIC/pySCENIC**: Gene regulatory network inference from single-cell data

## Related Concepts
- [[Graph Cellular Automata]] - Arbitrary topology as computational substrate
- [[Update Rule as Fundamental Unit]] - Topology defines neighborhoods for update rules
- [[Hierarchical Composition]] - Network modules at different scales
- [[Degeneracy in Biological Systems]] - Multiple paths provide robustness
- [[Robustness and Evolvability]] - Topology shapes both properties
- [[Cross-Boundary Signaling]] - Long-range edges connect modules
- [[Local Interaction]] - Most edges are local; topology mediates locality

#network-topology #graph-theory #complex-networks #systems-biology #modularity #robustness
