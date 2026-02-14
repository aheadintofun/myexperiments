# Dose-Response Relationship

## Definition
The quantitative relationship between exposure magnitude (dose) and biological effect magnitude (response). Fundamental to pharmacology, toxicology, and systems biology. **Not all doses produce the same response—the dose determines the outcome.**

## Core Principle
$$\text{Response} = f(\text{Dose})$$

The function $f$ can be:
- **Linear**: Response proportional to dose
- **Threshold**: No effect below critical dose
- **Sigmoid**: Graded response saturating at high dose
- **Biphasic**: Different responses at low vs. high dose (hormesis)
- **All-or-none**: Binary switch at threshold

## Canonical Curve: Sigmoid (Hill Equation)

$$R = R_{\max} \frac{D^n}{EC_{50}^n + D^n}$$

where:
- $R$ = response
- $D$ = dose
- $EC_{50}$ = dose producing 50% maximal response
- $n$ = Hill coefficient (cooperativity)
- $R_{\max}$ = maximal response

### Key Parameters
- **Potency**: $EC_{50}$ (lower $EC_{50}$ = more potent)
- **Efficacy**: $R_{\max}$ (maximal achievable response)
- **Cooperativity**: $n > 1$ indicates positive cooperativity (steep response), $n < 1$ negative cooperativity

## Non-Monotonic Dose-Response

### Hormesis
See [[Bioinformatics/concepts/Hormesis]]: **Beneficial effect at low dose, harmful at high dose**.

$$f(D) = \begin{cases}
\text{beneficial} & D < D_{\text{opt}} \\
\text{neutral} & D = D_{\text{opt}} \\
\text{harmful} & D > D_{\text{opt}}
\end{cases}$$

**Examples**:
- Exercise: Moderate beneficial, excessive harmful
- Radiation: Low-dose stimulates repair, high-dose causes damage
- Oxidative stress: Low ROS signals, high ROS damages

### Biphasic Responses
Different mechanisms dominate at different doses:
- **Low dose**: Receptor activation, signaling pathways
- **High dose**: Off-target effects, toxicity, saturation

## Time Dependence: Temporal Patterns Matter
Dose-response can depend on **temporal pattern**, not just total dose (see [[Temporal Pattern Sensitivity]]):

- **Pulsatile**: Intermittent exposure
- **Continuous**: Constant exposure
- **Ramping**: Gradually increasing dose

Same total dose, different pattern → different response.

Example: Insulin signaling responds differently to pulsatile vs. continuous glucose.

## Context Dependence
Response can depend on context (see [[Context Conditionality]]):
- **Genetic background**: Same drug, different response in different individuals
- **Cell type**: Same molecule, different response in liver vs. brain
- **Prior exposure**: Tolerance, sensitization, priming
- **Microenvironment**: Tissue context modulates response

## Transfer Function Perspective
Dose-response is a [[Transfer Functions|transfer function]]:
- **Input**: Perturbation (drug, stress, signal)
- **Output**: Biological response
- **Frequency domain**: How does response depend on perturbation frequency?

$$H(\omega) = \frac{\text{Response}(\omega)}{\text{Dose}(\omega)}$$

Captures **dynamic range**, **sensitivity**, **saturation**.

## Therapeutic Window
Safe and effective dosing requires understanding the curve:

```
Toxic dose
    ↑
    |     ╱────  Toxicity
    |    ╱
    |   ╱
    |  ╱────── Therapeutic effect
    | ╱
    |╱
    └──────────→ Dose
    Subtherapeutic
```

**Therapeutic window**: Dose range producing desired effect without toxicity.

**Narrow window**: Small margin of safety (chemotherapy, warfarin).
**Wide window**: Large safety margin (antibiotics, vitamins).

## Experimental Determination
1. **In vitro**: Cell culture with dose series, measure endpoint (proliferation, death, signaling)
2. **In vivo**: Animal models, dose escalation, measure physiological outcomes
3. **Clinical trials**: Phase I (safety, dose finding), Phase II (efficacy at selected doses)

## Computational Modeling
- **Pharmacokinetics (PK)**: How dose translates to concentration over time (ADME: absorption, distribution, metabolism, excretion)
- **Pharmacodynamics (PD)**: How concentration produces effect
- **PK-PD modeling**: Integrated prediction of dose → concentration → response

## Related Concepts
- [[Bioinformatics/concepts/Hormesis]] - Non-monotonic dose-response (beneficial at low dose)
- [[Pharmacological Hormesis]] - Therapeutic exploitation of hormesis
- [[Transfer Functions]] - Dose-response as input-output mapping
- [[Temporal Pattern Sensitivity]] - Time-dependent dose-response
- [[Context Conditionality]] - Context-dependent response
- [[Perturbation-Response-Adaptation]] - Dose as perturbation, response as adaptation

#dose-response #pharmacology #toxicology #hormesis #transfer-function #therapeutics
