# Critical Phenomena

## Definition
Universal behavior near phase transitions where systems exhibit scale-invariant properties. At the critical point, correlation length diverges, fluctuations occur at all scales, and power-law relationships replace exponential decay.

## Mathematical Structure

### Order Parameter
Quantity distinguishing phases:
$$m = \langle \phi \rangle$$

Examples:
- **Magnetization** (ferromagnet): $m = 0$ (disordered), $m \neq 0$ (ordered)
- **Density difference** (liquid-gas): $m = \rho_\text{liquid} - \rho_\text{gas}$
- **Infection prevalence** (epidemic): $m = I/N$

### Control Parameter
External variable tuned to reach critical point:
- Temperature $T$ (thermodynamics)
- Coupling strength $\beta$ (lattice models)
- Transmission rate $R_0$ (epidemiology)

### Phase Transition
$$m \sim |T - T_c|^\beta \quad \text{as } T \to T_c$$

Where $\beta$ is **critical exponent** (universal, independent of microscopic details).

## Critical Exponents

Near critical point, observables scale as power laws:

| Quantity | Scaling | Exponent | Meaning |
|----------|---------|----------|---------|
| Order parameter | $m \sim \|T - T_c\|^\beta$ | $\beta$ | How fast order emerges |
| Susceptibility | $\chi \sim \|T - T_c\|^{-\gamma}$ | $\gamma$ | Response to perturbations |
| Correlation length | $\xi \sim \|T - T_c\|^{-\nu}$ | $\nu$ | Spatial extent of correlations |
| Specific heat | $C \sim \|T - T_c\|^{-\alpha}$ | $\alpha$ | Energy fluctuations |

**Universality**: Systems with different microscopic details (Ising spins, lattice gas, alloy) share same exponents if they belong to same **universality class** (determined by symmetry, dimensionality).

## Scale Invariance
At $T = T_c$, no characteristic length scale. Zooming in/out reveals same statistical structure—**self-similarity**.

Correlation function:
$$C(r) \sim r^{-d+2-\eta}$$

Power-law (not exponential) decay.

## Biological Examples

### Epidemic Thresholds
**SIR model**: Susceptible → Infected → Recovered.

Basic reproduction number:
$$R_0 = \frac{\beta}{\gamma}$$

Where $\beta$ is transmission rate, $\gamma$ is recovery rate.

**Critical point**: $R_0 = 1$.
- $R_0 < 1$: Epidemic dies out (subcritical)
- $R_0 > 1$: Epidemic spreads (supercritical)

Final outbreak size scales as:
$$I_\infty \sim (R_0 - 1)^\beta$$

Near threshold: Outbreak size extremely sensitive to $R_0$.

### Percolation Transitions
Random graph: Edges activated with probability $p$.

**Critical point**: $p = p_c$ where giant component emerges.

Biological applications:
- **Habitat fragmentation**: Patches connected, species disperse. Below $p_c$: isolated fragments. Above: spanning cluster.
- **Protein interaction networks**: Add edges randomly. At $p_c$, network becomes connected.
- **Neural networks**: Synaptic connectivity. Criticality hypothesis: brain operates near $p_c$ for optimal information processing.

### Criticality in Neural Systems
Hypothesis: Brain self-organizes to critical point between ordered (locked) and disordered (chaotic) dynamics.

Evidence:
- Neuronal avalanches follow power-law size distribution
- Optimal information transmission at criticality
- Maximizes dynamic range and computational capacity

### Morphogen Gradient Criticality
Some developmental systems may operate near critical points:
- Small changes in morphogen concentration → abrupt cell fate switch
- Ultrasensitivity via positive feedback (Hill coefficient $n \gg 1$)

## Ising Model (Paradigm)
Spins on lattice: $s_i = \pm 1$.

Hamiltonian:
$$H = -J \sum_{\langle i,j \rangle} s_i s_j - h \sum_i s_i$$

Where $J$ is coupling, $h$ is external field.

**Phase transition** at critical temperature $T_c$ (2D: $T_c \approx 2.27 J/k_B$).

Below $T_c$: Spontaneous magnetization (ordered phase).
Above $T_c$: Paramagnetic (disordered phase).

Ising model universality class describes:
- Ferromagnets
- Liquid-gas transitions
- Binary alloys
- Some lattice models in biology

## Renormalization Group
Framework for understanding universality and critical exponents.

**Key idea**: Coarse-grain system iteratively. At critical point, system looks same at all scales—**fixed point** of renormalization flow.

See [[Renormalization in Biological Systems]].

## Key Insight
Critical phenomena reveal that **macroscopic behavior near transitions is insensitive to microscopic details**. Systems as different as magnets, fluids, and epidemics exhibit same scaling laws. This universality suggests deep organizing principles.

In biology: Evolution may tune systems to critical points to maximize adaptability, responsiveness, and information processing.

## Related Concepts
- [[Symmetry Breaking in Biological Systems]] - Phase transitions break symmetry
- [[Turing Pattern Formation]] - Patterns emerge at instability threshold
- [[Perturbation-Response-Adaptation]] - Response diverges near critical points
- [[Renormalization in Biological Systems]] - Coarse-graining at criticality
- [[Lattice and Spatial Modeling Hub]] - Lattice models exhibit criticality

## Tags
#critical-phenomena #phase-transitions #universality #scaling #power-laws #ising-model #percolation #epidemiology #criticality-hypothesis
