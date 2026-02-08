# Trajectory in State Space

## Definition
A path through [[State Space]] representing the time-evolution of a biological system. The trajectory $x(t)$ maps time to system configuration, showing **where the system is now** and **where it's heading**.

## Mathematical Formulation
State space $\mathcal{S}$ contains all possible configurations. A trajectory is a curve:

$$\gamma: [0, T] \to \mathcal{S}$$

where $\gamma(t) = x(t)$ is the system state at time $t$.

**Dynamics** (how trajectories evolve):

$$\frac{dx}{dt} = f(x, t)$$

The vector field $f$ determines trajectory direction at each point.

## Key Concepts

### Initial Conditions
- **Starting point**: $x(0) = x_0$
- **Trajectory determined**: Given $x_0$ and $f$, trajectory is unique (deterministic systems)
- **Sensitivity**: Nearby initial conditions may diverge (chaos) or converge (attractors)

### Attractors
See [[State Space]] for details. Trajectories converge to attractors:
- **Fixed point**: Homeostatic steady state
- **Limit cycle**: Oscillations (cell cycle, circadian rhythm)
- **Strange attractor**: Chaotic dynamics

### Bifurcations
See [[Trajectory and Branching Fate]]: Points where trajectory splits.
- **Developmental fate decisions**: Pluripotent → committed lineage
- **Phase transitions**: Healthy → disease state
- **Symmetry breaking**: Uniform → patterned

## Biological Examples

### Cell Differentiation
- **State space**: All possible gene expression profiles
- **Trajectory**: Pluripotent stem cell → differentiated cell type
- **Attractor**: Terminal differentiated state
- **Bifurcation**: Lineage commitment decision

### Protein Folding
- **State space**: All conformational angles (high-dimensional)
- **Trajectory**: Unfolded → native fold
- **Attractor**: Native structure (energy minimum)
- **Funnel landscape**: Many trajectories converge to same fold

### Ecosystem Succession
- **State space**: Species abundance vectors
- **Trajectory**: Bare ground → climax community
- **Attractor**: Stable ecosystem composition
- **Perturbation**: Fire, invasion → new trajectory

### Disease Progression
- **State space**: Physiological parameters, molecular signatures
- **Trajectory**: Healthy → pre-disease → disease
- **Intervention**: Therapeutic perturbation redirecting trajectory

## Constraints on Trajectories
See [[Constrained Dynamics]]: Not all paths are accessible.
- **Conservation laws**: Energy, mass, stoichiometry constrain trajectories
- **Physical constraints**: Excluded volume, bonding geometry
- **Biological constraints**: Genetic, developmental, evolutionary

Trajectories confined to constraint manifold.

## Perturbation and Response
[[Perturbation-Response-Adaptation]]: External perturbation pushes trajectory off course.
- **Acute response**: Immediate deflection
- **Return to baseline**: Trajectory returns to original attractor
- **Adaptation**: Attractor itself shifts (new baseline)

## Reversibility
- **Reversible**: Trajectory can be traversed backward (rare in biology)
- **Irreversible**: Development, aging, some phase transitions are one-way

**Developmental ratchet**: Differentiation is largely irreversible (requires reprogramming).

## Stochastic Trajectories
Deterministic: $dx/dt = f(x)$ (unique trajectory from $x_0$)
Stochastic: $dx = f(x)dt + g(x)dW$ (Brownian motion, noise)

**Result**: Cloud of trajectories from same $x_0$, converging to attractor distribution.

Biological relevance: Gene expression noise, molecular stochasticity.

## Computational Tools

### Numerical Integration
Solve $dx/dt = f(x)$ numerically:
- **Euler method**: $x_{n+1} = x_n + \Delta t \, f(x_n)$
- **Runge-Kutta**: Higher-order accuracy
- **Stochastic**: Gillespie algorithm for chemical master equation

### Phase Plane Analysis
Low-dimensional systems (2D-3D):
- Plot trajectories in phase space
- Identify attractors, separatrices, basins of attraction

### Dimensionality Reduction
High-dimensional state spaces (gene expression):
- **PCA**: Principal component analysis
- **t-SNE, UMAP**: Nonlinear manifold learning
- **Pseudotime**: Order cells along developmental trajectory

## Therapeutic Implications
- **Reprogramming**: Force trajectory toward desired state (iPSCs)
- **Cancer therapy**: Push tumor trajectory toward apoptosis, differentiation
- **Metabolic engineering**: Redirect metabolic flux trajectory

## Related Concepts
- [[State Space]] - Configuration space containing trajectories
- [[Trajectory and Branching Fate]] - Bifurcations in developmental trajectories
- [[Perturbation-Response-Adaptation]] - How perturbations affect trajectories
- [[Constrained Dynamics]] - Constraints confining trajectories
- [[Fitness Landscapes]] - Evolutionary trajectories through genotype space
- [[Morphogenesis]] - Developmental trajectory through morphospace

#trajectory #state-space #dynamics #attractor #differential-equations #systems-biology
