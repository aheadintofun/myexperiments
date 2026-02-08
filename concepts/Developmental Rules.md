# Developmental Rules

## Definition
Local gene-regulatory logic that maps **cell state + microenvironment** → **developmental outcome** (proliferation, differentiation, migration, apoptosis). In [[Graph Rewriting Automata]] formalism, these are the rewriting rules producing global organismal morphology.

## Structure of Developmental Rules
Each rule is a conditional:

**IF** (internal state AND neighbor signals AND position) **THEN** (action)

Examples:
- IF (progenitor state AND Wnt signal) THEN divide
- IF (high Shh AND low BMP) THEN differentiate to neural
- IF (mesenchymal state AND FGF signal) THEN migrate
- IF (damaged AND no neighbors) THEN apoptose

## Components

### Input: Local Configuration
From [[Local Configuration Space]]:
- **Cell state**: Gene expression profile, epigenetic marks
- **Neighbor signals**: Paracrine factors (Wnt, Hedgehog, BMP, Notch)
- **Mechanical cues**: Tension, compression, ECM stiffness
- **Positional information**: Morphogen gradient concentration

### Output: Developmental Action
- **Proliferation**: [[Vertex Division]] in graph formalism
- **Differentiation**: Change vertex state
- **Migration**: Move in space (rewire edges in spatial graph)
- **Apoptosis**: Delete vertex
- **Secretion**: Modify neighbor inputs (change edge weights)

## Canonical Developmental Signaling Pathways
See [[Developmental Toolkit]] for complete list. Major pathways:

### Hedgehog (Hh)
- **Input**: Smoothened activation
- **Output**: Gli transcription factors
- **Developmental role**: Dorsal-ventral patterning, digit number
- **Rule example**: IF (Shh > threshold) THEN ventral neural tube fate

### Wnt
- **Input**: Wnt ligand, Frizzled receptor
- **Output**: β-catenin stabilization
- **Developmental role**: Axis formation, stem cell maintenance
- **Rule example**: IF (Wnt AND no APC) THEN proliferate

### BMP (Bone Morphogenetic Protein)
- **Input**: BMP ligand, Smad signaling
- **Output**: Smad-mediated transcription
- **Developmental role**: Dorsal-ventral patterning, bone formation
- **Rule example**: IF (BMP high) THEN dorsal fate

### Notch (Lateral Inhibition)
- **Input**: Delta (neighbor) binds Notch (self)
- **Output**: NICD transcriptional activation
- **Developmental role**: Fine-grained patterning, neurogenesis
- **Rule example**: IF (neighbors high Delta) THEN non-neural fate

### FGF (Fibroblast Growth Factor)
- **Input**: FGF ligand, RTK activation
- **Output**: MAPK/ERK signaling
- **Developmental role**: Mesoderm induction, limb bud growth
- **Rule example**: IF (FGF AND competent state) THEN mesoderm

## Rules as Gene Regulatory Networks (GRNs)
Developmental rules implemented as GRN circuits:

**Example: Anterior-posterior patterning (Drosophila)**
- **Inputs**: Maternal gradients (Bicoid, Nanos)
- **Gap genes**: Hunchback, Krüppel, etc. (broad domains)
- **Pair-rule genes**: Even-skipped, Fushi-tarazu (stripes)
- **Segment polarity genes**: Engrailed, Wingless (refined segments)
- **Hox genes**: Specify segment identity

Each layer refines pattern from layer above. Final rule: "IF (Hox code = XYZ) THEN segment N identity"

## Modularity and Reuse
Developmental rules are modular:
- **Same pathway, different contexts**: Wnt in axis formation, limb development, hair follicles
- **Combinatorial logic**: Multiple pathways integrate to specify outcome
- **Evolutionary conservation**: Hox genes, Pax6, Dlx across phyla

This modularity = efficient genetic encoding. Small rule library → complex organisms via recombination.

## Graph Rewriting Interpretation
In [[Morphogenesis as Graph Rewriting]]:

**Developmental rule** = local rewriting rule on cellular graph
- Input: Vertex state + neighbor states
- Output: State update + topology change

**Example: Neural induction**
- **Rule**: IF (ectodermal state AND inhibit-BMP signal) THEN neural fate
- **Graph**: No topology change (state update only)
- **Biology**: Ectoderm → neural ectoderm (differentiation)

**Example: Limb bud outgrowth**
- **Rule**: IF (limb progenitor AND FGF > threshold) THEN divide
- **Graph**: Vertex division (growth)
- **Biology**: Apical ectodermal ridge maintains proliferation

## Temporal Sequencing
Developmental rules execute in specific order:
1. **Maternal effect genes** → initial polarity
2. **Gap genes** → coarse domains
3. **Pair-rule genes** → refinement
4. **Segment polarity** → maintenance
5. **Hox genes** → identity specification
6. **Organogenesis** → tissue-specific programs

Ordering matters: Later rules assume earlier patterns established.

## Robustness Mechanisms
Developmental rules include error-correction:

**Feedback loops**:
- Secreted inhibitors buffer gradients
- Cross-repression sharpens boundaries

**Redundancy**:
- Multiple pathways specify same outcome (degeneracy)
- Fail-safe if one pathway mutated

**Scaling**:
- Rules scale with embryo size (morphogen gradient ratios)
- Same rules → different sized organisms

See [[Robustness and Evolvability]].

## Related Concepts
- [[Graph Rewriting Automata]] - Formal framework for developmental rules
- [[Morphogenesis as Graph Rewriting]] - Development via rule iteration
- [[Developmental Toolkit]] - Catalog of conserved genetic programs
- [[Local Configuration Space]] - Input domain for rules
- [[Rule Space and Numbering]] - Space of possible developmental programs
- [[Cell Division as Vertex Division]] - Proliferation rule output
- [[Emergent Global Pattern]] - Global morphology from local rules
- [[Morphogenesis]] - Biological process governed by rules
- [[Turing Pattern Formation]] - Spatial patterning mechanism
- [[Hierarchical Composition]] - Nested rule application across scales

#development #gene-regulation #morphogenesis #signaling-pathways #developmental-biology #graph-rewriting #rules
