# Cell Division as Vertex Division

## Definition
The mathematical abstraction of **mitosis** as a graph rewriting operation: a parent cell (vertex) transforms into daughter cells (complete subgraph), inheriting the parent's intercellular connections (edges).

## Graph-to-Biology Mapping

| Graph Element | Biological Counterpart |
|---------------|------------------------|
| Vertex | Cell |
| Edge | Cell-cell adhesion, gap junction, signaling contact |
| Vertex state | Gene expression profile, cell type |
| Vertex division | Mitosis/cytokinesis |
| Daughter subgraph | Sister cells post-division |
| Edge inheritance | Maintained adhesions, inherited contacts |

## Division Operation
Parent cell $C_p$ with $n$ neighbors $\{N_1, N_2, ..., N_n\}$:

**Before division**:
- Graph: Single vertex $C_p$ connected to $\{N_i\}$
- Biology: Mother cell adhered to neighboring cells

**After division** (into 2 daughters $C_1, C_2$):
- Graph: Subgraph $K_2$ (edge $C_1 \leftrightarrow C_2$), connections distributed to $\{N_i\}$
- Biology: Sister cells touching, inheriting parent's adhesions

## Why Daughters Form Complete Subgraph?
Immediate post-division:
- **Physically adjacent**: Daughters touching at cleavage plane
- **Cytoplasmic continuity** (brief): Membrane neck before complete separation
- **Shared signals**: Exchange molecules before full separation
- **Mechanical coupling**: Linked by midbody initially

Later dynamics may break daughter-daughter edge if cells migrate apart.

## State Inheritance
Daughters inherit parent's state (approximately):
- **Genetic identity**: Identical DNA (barring mutations)
- **Epigenetic marks**: Histone modifications, methylation patterns
- **Cytoplasmic factors**: Proteins, mRNAs partitioned
- **Polarity cues**: Asymmetric division can create different states

In GRA: $s_{C_1}, s_{C_2} \approx s_{C_p}$ (with noise/asymmetry possible)

## Division Rules = Cell Cycle Regulation
In [[Graph Rewriting Automata]], division triggered by [[Local Configuration Space]]:

**Biological decision**: Divide or not?
- **Internal state**: Cyclin levels, DNA damage checkpoints
- **External signals**: Growth factors, contact inhibition
- **Configuration**: Cell state + neighbor states

**GRA rule**: If (state = proliferative AND neighbors < threshold) → divide

This captures:
- **Contact inhibition**: High neighbor density → no division
- **Growth factor dependence**: Proliferative state requires signals
- **Spatial regulation**: Division depends on local context

## Tissue as Evolving Graph
Developmental morphogenesis = iterative vertex division:

**Embryogenesis**:
- $t=0$: Single vertex (zygote)
- $t=1$: $K_2$ (2-cell stage)
- $t=2$: 4 vertices (4-cell stage)
- $t=n$: Blastula, gastrula, ... → adult (trillions of vertices)

Topology encodes:
- **Spatial organization**: Edges = physical adjacency
- **Lineage relationships**: Daughter proximity
- **Tissue architecture**: Clusters = organs

See [[Morphogenesis as Graph Rewriting]].

## Edge Dynamics Post-Division
After division, edges can:
- **Persist**: Daughters remain neighbors (epithelial sheet)
- **Strengthen**: Increased adhesion (cohesive tissue)
- **Weaken**: Reduced contact (cells migrate apart)
- **Break**: Daughters separate (mesenchymal cells)

Dynamics depend on cell type:
- **Epithelia**: Maintain connectivity (sheet integrity)
- **Mesenchyme**: Break connections (migration)
- **Neural**: Extend new connections (axon guidance)

## Asymmetric Division
Daughters can have different states:
- **Stem cell division**: Stem cell + differentiated progeny
- **Neurogenesis**: Neuron + progenitor
- **Polarity**: Apical/basal daughters

In GRA: Division rule assigns distinct states to daughters based on parent's polarization signals.

## Related Concepts
- [[Graph Rewriting Automata]] - Computational framework
- [[Vertex Division]] - Mathematical operation
- [[Dynamic Graph Topology]] - Topology evolves via division
- [[Morphogenesis as Graph Rewriting]] - Development as graph evolution
- [[Tissue Topology]] - Tissues as graphs
- [[Growth Dynamics in Networks]] - Network expansion via division
- [[Local Configuration Space]] - Context determining division
- [[Developmental Toolkit]] - Genetic programs controlling division

#cell-division #mitosis #graph-rewriting #morphogenesis #developmental-biology #tissue-modeling
