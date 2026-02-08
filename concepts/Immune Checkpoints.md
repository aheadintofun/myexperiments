# Immune Checkpoints

## Definition
Inhibitory signaling pathways that regulate immune activation, preventing excessive or prolonged responses. Checkpoints are the **brakes on the immune system**—essential for maintaining tolerance, preventing autoimmunity, and limiting tissue damage. Cancer exploits these brakes to evade immunity.

## Rationale for Checkpoints

**Why brakes are necessary**:
- Unchecked activation → autoimmunity, tissue damage
- Prolonged inflammation → chronic disease
- Energy cost of immune responses is high
- **Tradeoff**: Protect against self-attack vs maintain anti-pathogen/anti-tumor immunity

Checkpoints enforce **restraint**—the immune system must be powerful but controlled.

## Major Checkpoint Pathways

### CTLA-4 (Cytotoxic T-Lymphocyte Antigen 4)
**Expression**: Activated T cells, Tregs (constitutive)
**Ligands**: B7-1 (CD80), B7-2 (CD86) on APCs

**Mechanism**:
- Competes with CD28 for B7 binding (higher affinity than CD28)
- CD28 → activation signal; CTLA-4 → inhibitory signal
- **Effect**: Dampens T cell activation during priming phase

**Function**: Prevents excessive T cell activation early in immune response

**Knockout phenotype**: CTLA-4-/- mice die young from massive lymphoproliferation and multi-organ autoimmunity

### PD-1 (Programmed Cell Death 1)
**Expression**: Activated T cells, B cells, NK cells
**Ligands**: PD-L1 (B7-H1), PD-L2 (widely expressed, including tumors)

**Mechanism**:
- Engagement → SHP2 phosphatase recruitment → dephosphorylates TCR signaling molecules
- **Effect**: Suppresses T cell effector function, promotes apoptosis (exhaustion)

**Function**: Maintains peripheral tolerance, limits inflammation in tissues

**Upregulation**: Chronic antigen exposure (chronic infections, tumors) → T cell exhaustion

### LAG-3 (Lymphocyte Activation Gene 3)
**Ligands**: MHC II, LSECtin, galectin-3, FGL1
**Function**: Inhibits CD4+ T cell activation and Treg suppressive function
**Role**: Maintenance of Treg homeostasis, prevents autoimmunity

### TIM-3 (T cell Immunoglobulin and Mucin domain 3)
**Ligands**: Galectin-9, phosphatidylserine, CEACAM1
**Function**: T cell exhaustion marker, coinhibitory signal
**Expression**: Th1 cells, Tregs, innate immune cells

### TIGIT (T cell Immunoreceptor with Ig and ITIM domains)
**Ligands**: CD155, CD112 (Nectin family)
**Function**: Inhibits T cell and NK cell activation
**Mechanism**: Competes with activating receptor CD226 (DNAM-1)

## T Cell Exhaustion

**Definition**: Progressive loss of effector function due to chronic antigen exposure

**Characteristics**:
- Stepwise loss of functions: IL-2 production → TNF-α → IFN-γ → cytotoxicity
- Upregulation of multiple checkpoints (PD-1, LAG-3, TIM-3, TIGIT)
- Epigenetic remodeling → fixed exhausted state

**Contexts**:
- **Chronic viral infections**: HIV, HCV, HBV (virus persists despite immune response)
- **Cancer**: Tumor antigens present for months/years
- **Autoimmunity**: Chronic self-antigen exposure

**Reversibility**:
- Acute exhaustion: Reversible with checkpoint blockade
- Chronic exhaustion: Partially irreversible (epigenetic fixation)

## Checkpoint Blockade Immunotherapy

### Mechanism
Blocking inhibitory checkpoints releases immune responses:
- **Anti-CTLA-4** (ipilimumab): Enhances T cell priming
- **Anti-PD-1** (nivolumab, pembrolizumab): Restores effector function
- **Anti-PD-L1** (atezolizumab): Blocks tumor's "don't eat me" signal

**Result**: Reactivation of anti-tumor T cells → tumor killing

### Clinical Success
**FDA-approved indications** (20+ cancer types):
- Melanoma (first approval, 2011)
- Non-small cell lung cancer
- Renal cell carcinoma
- Hodgkin lymphoma
- Bladder cancer, colorectal cancer (MSI-high), many others

**Durable responses**: Some patients achieve complete remission lasting years

### Limitations
**Response rates**: 20-40% for most cancers (majority don't respond)

**Resistance mechanisms**:
- Lack of T cell infiltration (cold tumors)
- Antigen loss (no target for T cells)
- Alternative checkpoints (compensatory upregulation)
- Immunosuppressive microenvironment (Tregs, MDSCs)

**Predictive biomarkers**:
- PD-L1 expression (imperfect)
- Tumor mutational burden (more neoantigens → better response)
- Microsatellite instability (MSI-high tumors respond well)

### Immune-Related Adverse Events (irAEs)
**Autoimmunity** from removing brakes:
- Colitis, pneumonitis, hepatitis (inflammation of organs)
- Thyroiditis, hypophysitis (endocrine dysfunction)
- Type 1 diabetes (rare but severe)
- Dermatologic reactions (rash, vitiligo)

**Frequency**: 60-90% experience some irAE, 10-20% severe (grade 3-4)

**Management**: Corticosteroids, interrupt therapy, supportive care

This demonstrates checkpoints are **essential**—removing them unleashes autoimmunity.

## Combination Strategies

**Rationale**: Checkpoints have non-redundant mechanisms
- **Anti-CTLA-4 + Anti-PD-1**: Synergistic (50-60% response in melanoma)
- **Higher toxicity**: Increased irAE risk with combinations

**Other combinations**:
- Checkpoint blockade + chemotherapy
- Checkpoint blockade + radiation (abscopal effect)
- Checkpoint blockade + targeted therapy
- Checkpoint blockade + CAR-T

## Checkpoint Agonism (Enhancing Brakes)

**Therapeutic use**: Autoimmune disease
- **Abatacept** (CTLA-4-Ig fusion protein): Binds B7, blocks costimulation (rheumatoid arthritis)

**Concept**: Strengthen brakes to suppress autoreactive T cells

## Evolutionary Perspective

Checkpoints are **conserved** across vertebrates:
- Present in fish, birds, mammals
- **Evolutionary pressure**: Balance protection vs self-attack
- Pathogens evolve to exploit checkpoints (viral PD-L1 homologs)
- Tumors co-opt developmental checkpoint programs

## Control Theory Perspective

**Feedback control**:
- **Negative feedback**: Checkpoints dampen activation (stability)
- **Setpoint**: Baseline immune tone
- **Disturbance**: Antigen exposure
- **Controller**: Checkpoint pathways adjust response magnitude

**Without checkpoints**: Unstable system (runaway positive feedback)

**With checkpoints**: Proportional control (response matches threat level)

## Related Concepts
- [[Immune Tolerance]] - Checkpoints enforce peripheral tolerance
- [[Autoimmunity]] - Checkpoint failure or blockade → autoimmunity
- [[Tumor Immune Evasion]] - Tumors exploit checkpoints
- [[T cell exhaustion]] - Checkpoint upregulation in chronic stimulation
- [[Danger Theory]] - Checkpoints modulate danger response threshold
- [[Inflammation as Phase Transition]] - Checkpoints prevent runaway inflammation
- [[Context Conditionality]] - Same antigen → different outcome depending on checkpoint status
- [[Antigen Presentation]] - Costimulation as checkpoint context

## Tags
#immune-system #checkpoints #CTLA-4 #PD-1 #PD-L1 #immunotherapy #cancer #autoimmunity #T-cell-exhaustion #tolerance #irAE
