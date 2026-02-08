# Immune Repertoire as Compressed Model

## Definition
The BCR/TCR repertoire is a compressed representation of possible pathogen space. Through combinatorial diversity generation and selection, the immune system maintains a finite set of receptor sequences capable of recognizing an astronomically large antigen universe. This is **information compression**: A generative model that can reconstruct (recognize) novel inputs from a learned latent space.

## The Compression Problem

**Challenge**:
- Possible pathogen antigens: ~10^15 - 10^20 distinct epitopes
- Possible receptor sequences: Theoretical diversity ~10^18 (BCR) and ~10^15 (TCR)
- Actual repertoire: ~10^8 distinct B cells, ~10^7 distinct T cells at any time

**Solution**: Generate diverse receptors through combinatorial recombination, then select those with useful binding properties. The repertoire is a **learned compression** of evolutionary pathogen experience.

## Diversity Generation Mechanisms

### V(D)J Recombination
Random assembly of receptor genes from germline segments:
- **BCR (Immunoglobulin)**:
  - Heavy chain: V (40-50 segments) × D (20-30) × J (6) = ~12,000 combinations
  - Light chain: V (40) × J (5) = ~200 combinations
  - Total: ~2.4 million heavy-light pairings

- **TCR (T cell receptor)**:
  - α chain: V (~50) × J (~50) = ~2,500 combinations
  - β chain: V (~50) × D (~2) × J (~12) = ~1,200 combinations
  - Total: ~3 million αβ pairings

### Junctional Diversity
Additional variation at V-D-J junctions:
- **N-additions**: Random nucleotides added by TdT enzyme
- **P-additions**: Palindromic sequences from hairpin opening
- **Deletions**: Random nucleotides removed during joining

This increases theoretical diversity to ~10^15-10^18 possible receptors.

### Somatic Hypermutation (B cells only)
After antigen encounter, B cells undergo rapid mutation in germinal centers:
- **Mutation rate**: ~10^-3 per base pair per division (1 million × normal rate)
- **Selection**: Higher-affinity variants preferentially survive
- **Result**: Affinity maturation—receptors evolve to better fit antigen

## Degeneracy and Cross-Reactivity

**Key compression principle**: Many receptors recognize the same antigen, and each receptor recognizes multiple antigens.

- **Degeneracy**: Multiple distinct receptors bind the same epitope (redundancy)
- **Cross-reactivity**: Single receptor binds multiple epitopes (generalization)

This is **lossy compression**—some information is lost, but coverage is broad. Similar to autoencoders: A finite latent space (repertoire) reconstructs high-dimensional input (antigen space).

## Repertoire as Learned Model

**Analogy to machine learning**:
- **Training data**: Evolutionary pathogen exposure (phylogenetic timescale)
- **Model parameters**: Germline V, D, J segments (selected by evolution)
- **Inference**: V(D)J recombination generates diverse "hypotheses" (receptors)
- **Testing**: Antigen binding selects correct "hypotheses" (clonal selection)
- **Updating**: Somatic hypermutation refines model (affinity maturation)

The repertoire is a **generative model** that can respond to novel antigens (zero-shot recognition) because it has learned the statistical structure of pathogen space.

## Repertoire Sequencing

Modern technologies sequence TCR/BCR repertoires (immune repertoire sequencing, RepSeq):
- **Tools**: immunarch, TRUST4, MIXCR, VDJtools
- **Applications**:
  - Cancer: Tumor-infiltrating lymphocyte repertoires
  - Vaccination: Tracking antigen-specific clonal expansion
  - Autoimmunity: Identifying autoreactive clones
  - Aging: Repertoire diversity declines with age

Repertoire data reveals the **learned structure** of immune memory.

## Thymic Selection as Training

**Positive selection**: T cells must recognize self-MHC (feature extraction constraint)
**Negative selection**: T cells must NOT strongly recognize self-antigens (avoid false positives)

This is **supervised learning with negative examples**: The thymus teaches "what NOT to recognize" (self).

## Information Theoretic Perspective

The repertoire encodes:
- **Shannon diversity**: Evenness of clone sizes (high diversity = many rare clones, low = oligoclonal)
- **Clonality**: Measure of repertoire concentration (infection → clonal expansion → reduced diversity)
- **Overlap**: Shared clones between individuals (public clones = convergent solutions to common antigens)

A healthy repertoire is **high-dimensional**—maximizing coverage of antigen space.

## Related Concepts
- [[Clonal Selection Theory]] - Selection mechanism acting on repertoire
- [[Affinity Maturation]] - Iterative refinement of selected clones
- [[Information Compression in Biology]] - Repertoire as compression algorithm
- [[Degeneracy in Biological Systems]] - Cross-reactivity as degeneracy
- [[Immunological Memory]] - Memory cells as compressed representation
- [[Self-Nonself Discrimination]] - Negative selection shapes repertoire
- [[Context Conditionality]] - Same receptor, different outcome in different contexts
- [[Fitness Landscapes]] - Affinity as fitness in sequence space

## Tags
#immune-system #repertoire #BCR #TCR #V(D)J-recombination #diversity #compression #degeneracy #information-theory #RepSeq
