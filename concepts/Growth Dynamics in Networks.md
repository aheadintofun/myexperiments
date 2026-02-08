# Growth Dynamics in Networks

## Definition
The temporal evolution of network size and structure through vertex/edge addition, driven by local rules. In biological systems, this models **tissue expansion, vascular development, neural wiring**, and other processes where network topology actively changes as the system grows.

## Growth Mechanisms

### Vertex Addition (Proliferation)
[[Vertex Division]] in [[Graph Rewriting Automata]]:
- New vertices added via division of existing vertices
- Daughters inherit parent's connections
- Biological: Cell division ([[Cell Division as Vertex Division]])

**Growth rate**: $dV/dt = r \cdot V$
- Exponential if constant division rate $r$
- Logistic if resource-limited: $dV/dt = r \cdot V \cdot (1 - V/K)$

### Edge Addition (Connection Formation)
New edges created between existing vertices:
- Random attachment: Connect to random vertex
- Preferential attachment: Connect to high-degree vertices (rich-get-richer)
- Proximity-based: Connect to spatial neighbors
- Homophily: Connect to similar-state vertices

Biological examples:
- Synaptogenesis (neural development)
- Angiogenesis (vascular sprouting)
- Tissue fusion (wound healing)

### Edge Deletion (Pruning)
Edges removed based on activity, function:
- Synaptic pruning: Eliminate unused connections
- Vascular regression: Remove low-flow vessels
- Apoptosis-driven: Dead cells lose all edges

Balances growth, prevents over-connectivity.

## Preferential Attachment (Barabási-Albert Model)
**Rule**: New vertex connects to existing vertex $v$ with probability $\propto \deg(v)$

**Outcome**: Scale-free network
$$P(k) \sim k^{-\gamma}$$
- Power-law degree distribution
- Hubs (high-degree vertices) emerge
- Robust to random failures, vulnerable to targeted attacks

**Biological examples**:
- Protein interaction networks
- Metabolic networks
- Some neural circuits

## Spatial Growth
Growth constrained by geometry:
- New vertices added near parent (spatial locality)
- Edges form between nearby vertices (distance-dependent)
- Fractal branching patterns (trees, vasculature)

**Example: Diffusion-limited aggregation (DLA)**
- Particles add to cluster boundary via random walk
- Fractal structure emerges
- Models: Bacterial colonies, electrodeposition, coral growth

## Biological Growth Dynamics

### Vascular Networks
**Growth rule**: Endothelial tip cells extend toward VEGF gradient
- Branching: Tip cell sprouts, stalk cells follow
- Anastomosis: Tip cells fuse when they meet
- Regression: Low-flow vessels pruned

**Result**: Hierarchical tree optimized for transport

See [[Tissue Topology]] for vascular graph properties.

### Neural Networks
**Development**:
- Axon guidance: Growth cone navigates via chemoattractants/repellents
- Target selection: Synapse formation at target
- Pruning: Activity-dependent synaptic elimination (Hebbian: "neurons that fire together, wire together")

**Result**: Small-world network (efficiency + modularity)

### Bacterial Colonies
**Growth rule**: Cells divide, daughter cells adhere or disperse
- Biofilm: Cells remain connected (dense graph)
- Planktonic: Cells disperse (sparse graph)
- Pattern formation: Depends on nutrient availability, quorum sensing

**Result**: Fractal or dendritic colonies

### Plant Root Systems
**Growth rule**: Root tips extend, branch based on local water/nutrient gradients
- Branching frequency: Higher in nutrient-rich patches
- Tropisms: Gravitropism, hydrotropism guide direction

**Result**: Space-filling network optimized for resource acquisition

## Growth Arrest and Size Control
Mechanisms stopping growth:

**Contact inhibition**:
- Cells stop dividing when surrounded by neighbors
- In GRA: IF (degree > threshold) THEN no division
- Prevents over-proliferation

**Resource depletion**:
- Growth limited by nutrients, oxygen, space
- Logistic growth model: $dV/dt = r V (1 - V/K)$

**Programmed termination**:
- Developmental programs specify final size
- Replicative senescence (Hayflick limit)

**Negative feedback**:
- Growth factors stimulate inhibitor production
- Self-limiting signaling

## Mathematical Formalization
Network growth as dynamical system:

**Vertex dynamics**:
$$V(t+1) = V(t) + \Delta V(t)$$
where $\Delta V$ depends on local rules (division, deletion)

**Edge dynamics**:
$$E(t+1) = E(t) + \Delta E_{\text{add}} - \Delta E_{\text{remove}}$$

**Coupled**: Vertex addition often creates edges (division), vertex deletion removes edges (apoptosis).

Full graph dynamics: $G(t) \to G(t+1)$ via [[Graph Rewriting Automata]] rules.

## Network Metrics During Growth
Tracking topology evolution:

**Size**: $|V(t)|$, $|E(t)|$ over time

**Degree distribution**: $P(k, t)$ - does it converge to scale-free, Poisson, etc.?

**Clustering**: $C(t)$ - does local structure emerge?

**Path length**: $L(t)$ - does small-world property develop?

**Modularity**: Do communities form?

## Related Concepts
- [[Graph Rewriting Automata]] - Framework for growth dynamics
- [[Vertex Division]] - Primary growth mechanism
- [[Dynamic Graph Topology]] - Topology evolution
- [[Cell Division as Vertex Division]] - Biological interpretation
- [[Morphogenesis as Graph Rewriting]] - Developmental growth
- [[Tissue Topology]] - Resulting network structures
- [[Network Topology]] - Static graph properties
- [[Preferential Attachment]] - Growth rule generating scale-free networks
- [[Self-Organization in Graphs]] - Emergent structure from growth
- [[Organic Structure Emergence]] - Biological-looking growth patterns

#network-growth #dynamics #graph-theory #development #morphogenesis #vasculature #neural-development #topology-evolution
