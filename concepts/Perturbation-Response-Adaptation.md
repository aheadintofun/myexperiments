# Perturbation-Response-Adaptation

## Definition
The universal biological cycle: a system in baseline state receives a perturbation, exhibits a response trajectory, and settles into an adapted endpoint. This is the **genotype-phenotype map in motion**—not static, but a dynamic transfer function.

## Canonical Structure
1. **Baseline state**: Equilibrium before perturbation
2. **Perturbation**: External force (drug, antigen, CRISPR edit, drought)
3. **Response trajectory**: Transient dynamics through state space
4. **Adapted endpoint**: New equilibrium (resistant, tolerant, memory)
5. **Selection**: What variants were favored during adaptation?

## Domain Examples

### Drug Treatment
- Baseline: Pre-treatment tumor or pathogen
- Perturbation: Chemotherapy, antibiotic, immunotherapy
- Response: Cell death, stress response activation
- Adaptation: Resistant subclones emerge
- Selection: Drug-resistant mutations expand

### Immune Challenge
- Baseline: Naive immune repertoire
- Perturbation: Pathogen exposure
- Response: Clonal expansion of antigen-specific cells
- Adaptation: Memory cell formation, affinity maturation
- Selection: High-affinity clones dominate

### Environmental Stress (Agriculture)
- Baseline: Optimal growth conditions
- Perturbation: Drought, heat, pathogen attack
- Response: Stress pathway activation
- Adaptation: Tolerant cultivars survive
- Selection: Stress-resistant alleles increase frequency

### Genetic Perturbation
- Baseline: Wild-type organism
- Perturbation: CRISPR knockout, overexpression
- Response: Compensatory pathway activation
- Adaptation: Genetic buffering, synthetic rescue
- Selection: Epistatic modifier variants

## Mathematical Representation
Transfer function:
$$\mathbf{x}(t) = \mathcal{T}(\mathbf{x}_0, \mathbf{p}, \mathbf{c})$$

Where:
- $\mathbf{x}(t)$: State trajectory
- $\mathbf{x}_0$: Initial state
- $\mathbf{p}$: Perturbation parameters
- $\mathbf{c}$: Context vector

## Key Insight
The response is not instantaneous state change but a **trajectory**. The path through state space contains information about mechanism, constraints, and evolutionary potential.

## Related Concepts
- [[Trajectory and Branching Fate]] - Response as trajectory through state space
- [[Clonal Architecture and Selection]] - Selection during adaptation
- [[Context Conditionality]] - Response depends on context
- [[Hormesis]] - Beneficial response to controlled stress
- [[Temporal Pattern Sensitivity]] - Temporal structure of perturbation matters
- [[Variant-Phenotype Mapping]] - Genetic basis of response variation

## Tags
#perturbation #adaptation #stress-response #drug-resistance #evolutionary-dynamics #transfer-function #systems-biology
