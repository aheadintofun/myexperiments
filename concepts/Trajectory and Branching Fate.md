# Trajectory and Branching Fate

## Definition
Biological systems traverse **branching state space landscapes** where paths diverge at critical decision points. Development, disease progression, differentiation, crop maturation—all are dynamical systems with trajectory structure.

## Universal Pattern
- Initial state (zygote, stem cell, healthy tissue, seedling)
- Trajectory through high-dimensional state space
- **Bifurcation points** where fates diverge
- Terminal states (differentiated cell, disease endpoint, mature plant)
- Path determines outcome, not just initial/final state

## Mathematical Framework
- **Pseudotime**: Ordering cells along developmental trajectory
- **Trajectory inference**: Reconstructing branching paths from snapshots
- **Bifurcation analysis**: Identifying decision points
- **Attractors**: Stable terminal states

## Examples Across Biology

### Cellular Differentiation
Hematopoietic stem cell → lymphoid/myeloid lineages:
- Continuous trajectory through gene expression space
- Bifurcations at progenitor stages
- Terminal differentiation as attractor

### Disease Progression
Cancer natural history:
- Normal tissue → dysplasia → carcinoma in situ → invasive → metastatic
- Branch points: treatment response vs resistance
- Multiple paths to same endpoint (convergent evolution)

### Plant Development
Vegetative → reproductive transition:
- Photoperiod/vernalization trigger state change
- Meristem fate decisions
- Growth trajectory affected by environmental signals

## Computational Tools
- **Trajectory inference**: Monocle, PAGA, Slingshot, RNA velocity
- **Branching detection**: STREAM, URD
- **Attractor identification**: SCENT, Hopland

## Key Insight
The **trajectory itself contains information** not present in snapshots. Two cells in the same state arrived via different paths may have different future fates.

## Related Concepts
- [[Multi-Scale Lattice]] - Trajectories occur within hierarchical state spaces
- [[Perturbation-Response-Adaptation]] - External forces deflect trajectories
- [[Symmetry Breaking in Biological Systems]] - Bifurcations break symmetry
- [[Context Conditionality]] - Trajectory depends on context vector
- [[Clonal Architecture and Selection]] - Population-level trajectories through fitness landscapes

## Tags
#trajectory-inference #differentiation #development #branching #pseudotime #dynamical-systems #attractors
