# Local Configuration Space

## Definition
The set of all possible local states that determine a vertex's next state and topology changes in [[Graph Rewriting Automata]]. Local configuration = vertex state + states of all neighbors.

## Mathematical Structure
For vertex $v$ with state $s_v$ and neighborhood $\mathcal{N}(v)$:

**Local configuration**: $C_v = (s_v, \{s_u : u \in \mathcal{N}(v)\})$

**Configuration space size** (for $d$-regular graphs with binary states):
- Vertex state: 2 possibilities (0 or 1)
- Each of $d$ neighbors: 2 possibilities
- **Total configurations**: $2^{d+1}$

## Generalization to Non-Regular Graphs
For arbitrary topology:
- Neighborhood size varies by vertex
- Configuration space dimension varies
- Rules must handle variable-degree vertices
- Can use canonical ordering or degree-invariant statistics

## Rule Definition Over Configuration Space
A rewriting rule maps each local configuration to:
1. **Next state**: $s_v(t+1)$
2. **Topology change**: divide, add/remove edges, etc.

For $2^{d+1}$ configurations, rule specifies outcome for each.

Example (binary states, $d=2$ regular):
- 8 possible configurations (vertex: 0/1, neighbor 1: 0/1, neighbor 2: 0/1)
- Rule assigns next state + topology action to each of 8 cases

## Connection to Cellular Automata
[[Cellular Automata Framework]] uses same principle:
- CA: Local configuration = cell state + neighbor states
- Elementary CA (Wolfram): 8 configurations → 8 outputs
- [[Update Rule as Fundamental Unit]]: State transition from local config

**GRA extension**: Configuration also determines **topology changes**, not just state updates.

## Configuration-Dependent Dynamics
Different configurations → different behaviors:

| Configuration Example | Potential Outcome |
|----------------------|-------------------|
| Vertex=1, all neighbors=1 | Quiescence (stable, no division) |
| Vertex=1, all neighbors=0 | Division (isolated signal → growth) |
| Vertex=0, mixed neighbors | State flip (influenced by majority) |
| Vertex=1, >threshold neighbors=1 | Contact inhibition (no division) |

## Biological Interpretation
Local configuration represents cell's **decision-making context**:
- Own state = internal gene expression
- Neighbor states = paracrine signals, contact inhibition, mechanical stress
- Configuration → phenotypic outcome (proliferate, differentiate, migrate, die)

See [[Microenvironment Context]] for biological analog.

## Computational Complexity
**State space explosion**:
- $k$ states per vertex
- $d$ neighbors
- $k^{d+1}$ configurations per rule
- Exploring all rules: $k^{k^{d+1}}$ possibilities

See [[Rule Space and Numbering]] for enumeration strategies.

## Related Concepts
- [[Graph Rewriting Automata]] - Framework using local configurations
- [[Rule Space and Numbering]] - Enumerating rules over configurations
- [[Cellular Automata Framework]] - CA analog with fixed topology
- [[Local Interaction]] - Why local configurations suffice
- [[Update Rule as Fundamental Unit]] - Algebraic primitive mapping configurations
- [[Microenvironment Context]] - Biological analog
- [[Network Topology]] - Determines neighborhood structure

#graph-rewriting #automata #local-interaction #configuration-space #rule-systems
