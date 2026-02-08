# Vertex Division

## Definition
The fundamental growth operation in [[Graph Rewriting Automata]]: a single vertex transforms into a **complete subgraph** (typically $K_n$ with small $n$), inheriting the parent's connections and distributing them to daughter vertices.

## Mathematical Operation
Parent vertex $v$ with degree $d$ and state $s_v$:

$$v \to K_n$$

where $K_n$ is a complete graph on $n$ vertices (all pairwise connected).

**Connection inheritance**:
- Each neighbor of $v$ connects to one or more daughters
- Daughters connected to each other (complete subgraph)
- Total degree approximately conserved or increased

## Biological Analog: Cell Division
Direct correspondence to mitosis:

| Graph Operation | Biological Process |
|-----------------|-------------------|
| Parent vertex | Mother cell |
| Daughter vertices | Daughter cells |
| Inherited edges | Cell-cell adhesions, signaling contacts |
| Vertex state | Cell type, gene expression state |
| Division rule | Cell cycle regulation, mitotic signals |

See [[Cell Division as Vertex Division]] for detailed mapping.

## Why Complete Subgraph?
Daughters initially maximally connected because:
- Physically adjacent after division (touching)
- Share cytoplasm during division → signaling contact
- Form local cluster before dispersing

Later dynamics may prune some daughter-daughter edges.

## Role in Morphogenesis
Vertex division enables:
- **Growth**: network expands from single vertex (zygote)
- **Tissue formation**: clusters of related cells (clones)
- **Spatial organization**: topology encodes physical proximity
- **Hierarchical structure**: lineage trees embedded in graph

See [[Morphogenesis as Graph Rewriting]].

## Local vs. Global Control
Division decisions are **local**:
- Depends on vertex state $s_v$
- Depends on neighborhood configuration $\{\mathcal{N}(v)\}$
- No global growth program
- Yet produces coordinated global patterns ([[Emergent Global Pattern]])

## Contrast with Other Graph Operations

| Operation | Topology Change | Biological Analog |
|-----------|----------------|-------------------|
| Vertex division | $V \to V + n$, $E$ increases | Cell division |
| Vertex deletion | $V \to V - 1$, $E$ decreases | Apoptosis |
| Edge addition/removal | $V$ constant, $E$ changes | Adhesion/detachment |
| Vertex state change | No topology change | Differentiation |

## Related Concepts
- [[Graph Rewriting Automata]] - Framework using vertex division
- [[Dynamic Graph Topology]] - Topology as dynamical variable
- [[Cell Division as Vertex Division]] - Biological interpretation
- [[Local Configuration Space]] - States determining division
- [[Morphogenesis as Graph Rewriting]] - Development via division
- [[Growth Dynamics in Networks]] - Network expansion mechanisms
- [[Tissue Topology]] - Biological tissues as graphs
- [[Hierarchical Composition]] - Emergent multi-scale structure from division

#graph-rewriting #growth #morphogenesis #cell-division #topology #automata
