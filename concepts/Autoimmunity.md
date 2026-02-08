# Autoimmunity

## Definition
Immune responses directed against self-antigens, resulting from failure of tolerance mechanisms. This is **boundary failure inward**—the phenotypic boundary erroneously classifies self as non-self, leading to immune-mediated tissue damage.

## Mechanisms of Autoimmunity

### Breakdown of Central Tolerance
**Thymic selection failures**:
- Incomplete deletion of self-reactive T cells
- AIRE mutations: Tissue antigens not expressed in thymus for tolerance induction (APECED syndrome)
- "Holes" in the negative selection repertoire

### Breakdown of Peripheral Tolerance
**Treg dysfunction**:
- FoxP3 mutations → IPEX syndrome (severe multi-organ autoimmunity)
- Reduced Treg numbers or impaired suppressive function
- Inflammatory cytokines override Treg suppression

**Loss of immune privilege**:
- Blood-brain barrier disruption → CNS antigen exposure
- Trauma releasing sequestered antigens (eye, testis)

### Molecular Mimicry
Pathogen epitopes resemble self-antigens:
- **Streptococcal M protein** resembles cardiac myosin → rheumatic fever
- **Campylobacter jejuni** gangliosides resemble nerve gangliosides → Guillain-Barré syndrome
- Initial anti-pathogen response cross-reacts with self

This is **misclassification via feature similarity**—the immune system generalizes incorrectly.

### Bystander Activation
Tissue damage releases self-antigens in inflammatory context:
- **Viral infection** causes tissue destruction
- Self-antigens presented with danger signals (DAMPs)
- Breaks tolerance: Previously ignored self-antigens now activate immune cells

### Epitope Spreading
Initial autoimmune response amplifies:
- Tissue damage releases additional self-antigens
- Immune response broadens to new epitopes
- **Diversification**: Initially narrow response becomes polyclonal

Autoimmunity becomes **self-sustaining** through positive feedback.

## Categories of Autoimmune Diseases

### Organ-Specific
Immune attack localized to one organ:
- **Type 1 diabetes**: T cells destroy pancreatic beta cells
- **Hashimoto's thyroiditis**: Antibodies against thyroid peroxidase
- **Multiple sclerosis**: T cells attack CNS myelin
- **Graves' disease**: Antibodies stimulate thyroid receptor (hyperthyroidism)

### Systemic
Widespread immune activation:
- **Systemic lupus erythematosus (SLE)**: Anti-nuclear antibodies, immune complex deposition
- **Rheumatoid arthritis**: Joint inflammation, anti-citrullinated protein antibodies
- **Sjögren's syndrome**: Salivary/lacrimal gland destruction
- **Systemic sclerosis**: Fibrosis, vascular damage

## Genetic Susceptibility

**HLA associations**:
- **HLA-DR4**: Rheumatoid arthritis (4× risk)
- **HLA-B27**: Ankylosing spondylitis (90× risk)
- **HLA-DQ2/DQ8**: Celiac disease (required for disease)

**Non-HLA genes**:
- **PTPN22**: Protein tyrosine phosphatase (multiple autoimmune diseases)
- **CTLA-4**: Immune checkpoint (RA, T1D, thyroid disease)
- **IL2RA**: IL-2 receptor alpha chain (T1D, MS)

Genetics provide susceptibility; environmental triggers initiate disease.

## Environmental Triggers

- **Infections**: Molecular mimicry, bystander activation
- **Microbiome dysbiosis**: Loss of commensal tolerance signals
- **UV exposure**: SLE flares (apoptotic cell clearance defects)
- **Smoking**: Rheumatoid arthritis (citrullination of proteins)
- **Vitamin D deficiency**: MS, T1D (immune regulation)

Autoimmunity arises from **gene-environment interactions**.

## Immune Checkpoint Inhibitor-Induced Autoimmunity

Cancer immunotherapy (anti-CTLA-4, anti-PD-1) releases brakes:
- **Intended effect**: Activate anti-tumor immunity
- **Side effect**: Autoimmune toxicities (colitis, pneumonitis, thyroiditis, T1D)

This demonstrates tolerance is **actively maintained**—removing checkpoints unleashes autoimmunity.

## Therapeutic Strategies

### Suppression
- **Corticosteroids**: Broad immunosuppression
- **DMARDs**: Disease-modifying antirheumatic drugs (methotrexate)
- **Biologics**: Anti-TNF (infliximab), anti-IL-6 (tocilizumab), anti-CD20 (rituximab)

### Tolerance Restoration
- **Antigen-specific therapy**: Induce tolerance to specific self-antigens (experimental)
- **Treg expansion**: Adoptive transfer or IL-2 therapy
- **Oral tolerance**: Feeding antigen to induce mucosal tolerance

### Immune Reconstitution
- **HSCT**: Hematopoietic stem cell transplant (reboot immune system)
- **CAR-Treg therapy**: Engineered Tregs targeting specific tissues

## Autoimmunity as Misclassification

From a machine learning perspective:
- **Ground truth**: Self vs non-self labels
- **Training error**: Incomplete negative selection (thymus)
- **Generalization error**: Molecular mimicry (pathogen resembles self)
- **Drift**: Environmental changes alter self-antigen presentation
- **Result**: False positives (autoimmunity)

The immune system is an **imperfect classifier** trading off sensitivity (catch all pathogens) vs specificity (avoid self-attack).

## Related Concepts
- [[Immune Tolerance]] - Mechanisms that fail in autoimmunity
- [[Self-Nonself Discrimination]] - Misclassification underlying autoimmunity
- [[Danger Theory]] - Bystander activation via danger signals
- [[Figure-Ground Decomposition]] - Frame inversion: Self becomes foreground (target)
- [[Molecular mimicry]] - Feature similarity causing misclassification
- [[Immune Checkpoints]] - Checkpoint inhibition induces autoimmunity
- [[Microbiome Negotiation]] - Dysbiosis breaks commensal tolerance
- [[Context Conditionality]] - Same self-antigen → tolerance or immunity depending on context

## Tags
#immune-system #autoimmunity #tolerance-failure #self-attack #rheumatoid-arthritis #lupus #type1-diabetes #multiple-sclerosis #molecular-mimicry #Tregs
