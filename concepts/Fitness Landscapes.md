# Fitness Landscapes

## Definition
A mapping from [[State Space|genotype space]] (or phenotype space) to fitness values. [[Evolutionary Tinkering|Evolution]] traverses this landscape via mutation and [[Clonal Selection Theory|selection]]—populations climb fitness peaks via adaptive walks.

## Mathematical Structure
Fitness function:
$$w = f(\mathbf{g})$$

Where:
- $\mathbf{g}$: Genotype vector (sequence, allele frequencies)
- $w$: Fitness (reproductive success, growth rate)

For population genetics:
$$\frac{d\mathbf{g}}{dt} \propto \nabla f(\mathbf{g})$$

Populations move up fitness gradients.

## Landscape Topography

### Smooth Landscapes
Additive effects: fitness contributions independent.
$$w(\mathbf{g}) = \sum_i \beta_i g_i$$

[[Evolutionary Tinkering|Evolution]] predictable: follows gradient to global optimum.

### Rugged Landscapes
Epistasis: fitness depends on genetic interactions.
$$w(\mathbf{g}_1 + \mathbf{g}_2) \neq w(\mathbf{g}_1) + w(\mathbf{g}_2)$$

Features:
- **Multiple local optima**: [[Evolutionary Tinkering|Evolution]] trapped on suboptimal peaks
- **Valleys**: Low-fitness intermediates between peaks
- **Ridges**: Accessible high-fitness paths through [[State Space|sequence space]]

## Sign Epistasis
The sign of a mutation's effect depends on genetic background.

Example: Mutation A beneficial alone, deleterious with mutation B.

$$\Delta w(A \mid \text{background}) > 0$$
$$\Delta w(A \mid B) < 0$$

Consequence: Accessible evolutionary paths constrained. Some sequences unreachable.

## NK Model
Kauffman's model for tunably rugged landscapes:
- $N$: Number of loci
- $K$: Number of epistatic interactions per locus

$K = 0$: Smooth (additive).
$K = N-1$: Maximally rugged (random).

Captures trade-off: evolvability vs robustness.

## Applications in Biology

### Protein Engineering
[[State Space|Sequence space]]: all possible amino acid sequences.
Fitness: enzymatic activity, [[Protein Structure Prediction|stability]], binding affinity.

Directed [[Evolutionary Tinkering|evolution]]: mutagenesis + [[Clonal Selection Theory|selection]] climbs fitness landscape.

Challenge: Astronomical [[State Space|sequence space]] ($20^{300}$ for 300-residue protein). [[Evolutionary Tinkering|Evolutionary]] search explores tiny fraction.

### Drug Resistance
Genotype: [[Tumor Immune Evasion|tumor]] mutation profile.
Fitness: [[Growth Dynamics in Networks|growth rate]] under drug [[Clonal Selection Theory|selection]].

Resistance mutations create new fitness peaks under treatment. Combination therapy aims to eliminate accessible peaks.

### Microbial Evolution
Laboratory evolution experiments:
- Adapt bacteria to new carbon source
- Adaptive walks from ancestral strain to evolved strain
- Map fitness landscape via saturation mutagenesis

Lenski long-term evolution experiment (E. coli, 70,000+ generations):
- Citrate utilization evolved via contingent mutations
- Historical contingency: some peaks require specific path

### Agricultural Breeding
Genotype: crop allele composition.
Fitness: yield, drought tolerance, disease resistance.

Genomic selection: predict fitness from genotype, select high performers.

## Context Dependence
Fitness landscapes are **not fixed**—they depend on [[Microenvironment Context|environment]].

$$w = f(\mathbf{g}, \mathbf{e})$$

Where $\mathbf{e}$ is [[Context Conditionality|environmental context]].

[[Genotype-to-Phenotype Hub|Genotype]] × [[Microenvironment Context|Environment]] interaction (G×E):
- Allele beneficial in one [[Microenvironment Context|environment]], deleterious in another
- Different landscapes in different [[Microenvironment Context|environments]]
- Balancing [[Clonal Selection Theory|selection]] maintains [[Degeneracy in Biological Systems|diversity]]

## Key Insight
Evolution does not see the global landscape—only local gradients. Populations climb nearest peak via small mutational steps. History matters: which peak reached depends on starting genotype and mutational path.

## Related Concepts
- [[Variant-Phenotype Mapping]] - Genotype-fitness is variant of genotype-phenotype
- [[Clonal Architecture and Selection]] - Selection dynamics on fitness landscape
- [[Degeneracy in Biological Systems]] - Neutral networks (equal fitness)
- [[Context Conditionality]] - Fitness landscapes depend on environment
- [[Perturbation-Response-Adaptation]] - Perturbation changes fitness landscape

## Tags
#fitness-landscapes #evolution #epistasis #selection #genotype-phenotype #NK-model #ruggedness #optimization
