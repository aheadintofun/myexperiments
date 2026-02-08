# Update Rule as Fundamental Unit

## Definition
In cellular automata frameworks, the recurring computational primitive is not the "cell" itself but the **update rule at the boundary between adjacent lattice sites**. This boundary interaction encodes the local algebra of the system.

## Why Boundaries Matter
- Information flows across site boundaries
- State transitions depend on neighborhood relationships
- The update rule captures the interaction physics/biology
- Global dynamics emerge from composition of local boundary rules

## Algebraic Structure
The update rule at a boundary defines:
- **Inputs**: States of adjacent sites
- **Transformation**: Function mapping neighborhood states to next state
- **Conservation laws**: What quantities are preserved
- **Symmetries**: What transformations leave the rule invariant

## Contrast with Cell-Centric View
- Cell-centric: "What happens inside each site?"
- Boundary-centric: "What happens when sites interact?"
- The latter captures the **relational** structure of the system

## Communication/Signaling Structure
The lattice topology encodes:
- Who can communicate with whom (connectivity)
- Strength of interactions (weighted edges)
- Directionality (asymmetric update rules)

## Implementation Insight
In heterogeneous lattices, different boundaries may have different update rules:
- Tissue-tissue boundary: One rule set
- Tissue-tumor boundary: Different rule set
- Immune cell-tumor boundary: Yet another rule set

This heterogeneity IS the biological specificity.

## Related Concepts
- [[Cellular Automata Framework]] - Overall computational structure
- [[Heterogeneous Lattice]] - Variable boundary rules
- [[Local Interaction]] - Neighborhood-dependent dynamics
- [[Emergent Global Pattern]] - Composition of local rules

## Tags
#cellular-automata #update-rule #local-interaction #boundary #algebra #fundamental-unit
