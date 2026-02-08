# Self-Nonself Discrimination

## Definition
The fundamental immunological problem: how to distinguish molecular patterns belonging to the organism (self) from foreign entities (non-self) that should trigger immune responses. This is the core computational challenge underlying adaptive immunity.

## The Recognition Problem

Every adaptive immune cell carries receptors (BCR for B cells, TCR for T cells) that recognize molecular patterns. The challenge:
- **Self molecules** vastly outnumber pathogens
- **Pathogen diversity** is astronomical (viruses, bacteria, fungi, parasites)
- **Cross-reactivity** means receptors bind multiple targets
- **Molecular mimicry** allows pathogens to resemble self

The immune system must classify molecules with near-perfect accuracy, as false positives (autoimmunity) and false negatives (infection) are both lethal.

## Mechanisms

### Central Tolerance (Thymus, Bone Marrow)
Developing lymphocytes undergo **thymic selection**:
- **Positive selection**: T cells that recognize self-MHC survive
- **Negative selection**: T cells with high self-affinity are deleted
- **Clonal deletion**: Autoreactive clones eliminated during development
- **AIRE protein**: Expresses tissue-specific antigens in thymus for tolerance induction

Result: Surviving T cells are self-MHC restricted but not self-reactive.

### Peripheral Tolerance (Tissues)
Additional mechanisms prevent autoimmunity after cells leave primary lymphoid organs:
- **Anergy**: Functional inactivation without costimulation
- **Regulatory T cells (Tregs)**: Active suppression of autoreactive cells
- **Immune privilege**: Brain, eye protected by blood-tissue barriers
- **Activation thresholds**: Require multiple signals to prevent spurious activation

## Burnet's Self-Nonself Theory

Frank Macfarlane Burnet (1949) proposed:
1. During development, immune system learns a catalog of self molecules
2. Any molecule encountered after this "learning period" is non-self
3. Self-reactive lymphocytes are deleted during ontogeny

This was revolutionary but incomplete—see [[Danger Theory]] for modern refinements.

## Computational Framing

Self-nonself discrimination is a **classification problem** in molecular space:
- **Training data**: Self molecules encountered during development
- **Test data**: Every molecule encountered during life
- **Loss function**: Minimize false positives (autoimmunity) AND false negatives (infection)
- **Regularization**: Tolerance mechanisms prevent overfitting to self

The immune system solves this with a distributed classifier ensemble (millions of B/T cell clones).

## Boundary Enforcement Perspective

Self-nonself discrimination IS phenotypic boundary definition. The immune system literally determines what belongs to the organism:
- **Self** = the phenotypic interior (to be preserved)
- **Non-self** = the phenotypic exterior (to be defended against)
- **Tolerance** = negotiated boundary (microbiome, fetus)

This is not predetermined genetics but **active computational enforcement**.

## Related Concepts
- [[Immune Tolerance]] - Mechanisms preventing self-attack
- [[Immunological Memory]] - Learning non-self patterns
- [[Danger Theory]] - Alternative framing: safe vs dangerous
- [[Figure-Ground Decomposition]] - Self as background, pathogen as foreground
- [[Immune Repertoire as Compressed Model]] - Receptor diversity samples molecular space
- [[Context Conditionality]] - Same molecule → different classification in different contexts
- [[Maternal-Fetal Tolerance]] - Paradoxical tolerance of non-self fetus

## Tags
#immune-system #self-nonself #recognition #tolerance #boundary #classification #thymic-selection #clonal-deletion
