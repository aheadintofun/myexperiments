# Temporal Pattern Sensitivity

## Definition
The phenomenon where the same molecular signal produces opposite biological outcomes depending on its temporal dynamics. Not just concentration matters, but the pattern over time: tonic vs phasic, chronic vs acute, pulsatile vs sustained.

## Canonical Example: IL-6

### Chronic Elevation (Cachexia)
- Sustained high IL-6 levels
- Drives systemic catabolism
- Muscle wasting, fat loss
- Inflammatory state
- Pathological outcome

### Pulsatile (Exercise)
- Brief IL-6 spike during exercise
- Triggers myokine signaling cascade
- Muscle adaptation, browning of adipose
- Metabolic health improvement
- Beneficial outcome

**Same molecule, different temporal pattern, opposite biological effect.**

## Other Examples

### Glucocorticoids
- Chronic: Muscle wasting, immunosuppression, osteoporosis
- Acute: Stress response, anti-inflammatory, metabolic mobilization

### Insulin
- Pulsatile: Normal glucose regulation
- Constant: Insulin resistance, metabolic dysfunction

### Growth Factors
- Pulsatile: Growth, differentiation
- Sustained: Oncogenic transformation

## Computational Implication
Lattice update rules must be time-pattern sensitive:
- Not just `state[t+1] = f(state[t], signal)`
- But `state[t+1] = f(state[t], signal_history)`

Requires temporal memory and pattern detection in update rules.

## Information Content
The temporal pattern IS part of the information being transmitted. Two signals with identical time-averaged concentration but different dynamics encode different information.

## Related Concepts
- [[Cachexia as Phase Transition]] - Chronic signaling drives pathology
- [[Cachexia Inversion]] - Pulsatile signaling drives adaptation
- [[Perturbation-Response-Adaptation]] - Temporal dynamics of response
- [[Cross-Boundary Signaling]] - Temporal patterns in signaling
- [[Bioinformatics/concepts/Hormesis]] - Beneficial temporal patterns of stress
- [[Context Conditionality]] - Temporal context affects outcomes
- [[Signal Processing in Biological Systems]] - Temporal decoding
- [[Cellular Automata Framework]] - Update rules with temporal memory

## Tags
#temporal-dynamics #signal-processing #pattern #chronic-vs-acute #biological-computation #context-dependent
