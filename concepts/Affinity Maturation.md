# Affinity Maturation

## Definition
The process by which B cells undergo iterative rounds of somatic hypermutation and selection in germinal centers, producing antibodies with progressively higher affinity for antigen. This is **real-time molecular evolution**—gradient descent on a fitness landscape defined by antigen binding affinity.

## Germinal Center Reaction

### Location and Structure
- **Secondary lymphoid organs**: Lymph nodes, spleen
- **Germinal centers (GCs)**: Specialized microanatomical structures arising 7-10 days post-antigen exposure
- **Dark zone**: Rapid B cell proliferation and somatic hypermutation
- **Light zone**: Antigen presentation by follicular dendritic cells (FDCs), selection by T follicular helper cells (Tfh)

### The Cycle

**1. Mutation (Dark Zone)**
- B cells divide rapidly (~6 hour doubling time)
- **Activation-induced cytidine deaminase (AID)** introduces point mutations in immunoglobulin variable regions
- Mutation rate: ~10^-3 per base pair per division (1 million × normal somatic mutation rate)
- Random mutations: Some increase affinity, most decrease affinity, some are neutral

**2. Selection (Light Zone)**
- Mutated B cells migrate to light zone
- Compete for antigen displayed on FDCs
- **High-affinity B cells** capture more antigen, receive survival signals from Tfh cells
- **Low-affinity B cells** fail to capture antigen, undergo apoptosis
- Surviving B cells return to dark zone for another round

**3. Iteration**
- Cycles repeat 10-20 times over 2-3 weeks
- Each iteration: Mutation → Selection → Amplification
- Result: Exponential improvement in antigen binding

## Molecular Mechanism

### Somatic Hypermutation (SHM)
**AID enzyme**:
- Deaminates cytosine → uracil in immunoglobulin genes
- Uracil recognized as abnormal base
- Repair pathways introduce mutations during correction
- **Hotspots**: AID prefers RGYW motifs (R=purine, Y=pyrimidine, W=A/T)

**Mutation spectrum**:
- Point mutations: C→T, G→A (direct deamination)
- A→G, T→C (error-prone repair)
- Small insertions/deletions (rare)

### Class Switch Recombination (CSR)
Concurrent process changing antibody effector function:
- Heavy chain constant region switches (IgM → IgG/IgA/IgE)
- Variable region (antigen binding) unchanged
- Same antigen specificity, different effector properties

## Fitness Landscape Perspective

**Sequence space**:
- Dimensions: ~300 nucleotides in variable region
- Landscape: Affinity as "height" (fitness)
- **Rugged landscape**: Multiple local optima, epistasis common

**Optimization dynamics**:
- **Mutation**: Random walk in sequence space
- **Selection**: Gradient ascent toward higher affinity
- **Population**: Multiple B cells explore landscape in parallel
- **Tradeoff**: Mutation rate balances exploration vs exploitation

This is **parallel stochastic gradient descent** with population-based exploration.

## Affinity Improvement

**Typical trajectory**:
- Naive B cell: Affinity constant $K_d \sim 10^{-6}$ M (weak binding)
- After 2 weeks GC reaction: $K_d \sim 10^{-9}$ M (strong binding)
- **~1000-fold improvement** in binding affinity

High-affinity antibodies:
- Neutralize pathogens more effectively
- Require lower concentrations for protection
- Provide stronger immune memory

## Convergent Evolution

Different individuals produce antibodies with:
- **Distinct sequences** (different mutation paths)
- **Similar structures** (converge on same binding solution)
- **Shared motifs** (public antibodies to common pathogens)

This is **convergent molecular evolution**—different starting points reach similar functional endpoints.

## Temporal Dynamics

**Early response** (days 1-7):
- Low-affinity IgM antibodies
- Broad cross-reactivity
- Germinal centers begin forming

**Middle response** (weeks 2-4):
- Germinal center maturation ongoing
- Affinity increasing
- Class switch to IgG

**Late response** (weeks 4+):
- High-affinity IgG antibodies
- Narrow specificity
- Memory B cells and long-lived plasma cells emerge

## Failure Modes

**Autoimmunity**:
- Mutations create self-reactive antibodies
- Normally deleted by selection checkpoints
- Failure → autoantibodies (lupus, rheumatoid arthritis)

**Lymphoma**:
- AID-induced mutations occasionally hit oncogenes (BCL6, MYC)
- Germinal center B cells → B cell lymphoma

High mutation rate is double-edged: Enables adaptation but risks pathology.

## Related Concepts
- [[Clonal Selection Theory]] - Population-level selection drives affinity maturation
- [[Immune Repertoire as Compressed Model]] - Maturation refines the model
- [[Fitness Landscapes]] - Affinity landscape in sequence space
- [[Immunological Memory]] - High-affinity memory B cells result from maturation
- [[Trajectory and Branching Fate]] - GC B cells differentiate into plasma cells vs memory cells
- [[Perturbation-Response-Adaptation]] - Antigen drives iterative adaptation
- [[Degeneracy in Biological Systems]] - Multiple sequences achieve similar affinity
- [[Context Conditionality]] - Tfh signals provide selection context

## Tags
#immune-system #affinity-maturation #germinal-center #somatic-hypermutation #selection #fitness-landscape #B-cells #antibodies #evolution #AID
