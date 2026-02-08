# Antigen Presentation

## Definition
The process by which cells display peptide fragments on Major Histocompatibility Complex (MHC) molecules for recognition by T cell receptors (TCRs). This is the **context-dependent signaling system** that determines whether T cells activate, tolerate, or ignore an antigen. Same peptide-MHC can trigger opposite outcomes depending on costimulatory context.

## MHC as Display System

### MHC Class I (All Nucleated Cells)
- **Structure**: Single α chain + β2-microglobulin
- **Peptide source**: Intracellular proteins (cytosolic degradation)
- **Binds to**: CD8+ T cells (cytotoxic T cells)
- **Function**: Display "self-snapshot"—cellular proteome surveillance

**Message**: "This is what I am making inside." Infected or cancerous cells display abnormal peptides.

### MHC Class II (Antigen-Presenting Cells)
- **Structure**: α and β chains
- **Peptide source**: Extracellular proteins (endosomal pathway)
- **Binds to**: CD4+ T cells (helper T cells)
- **Function**: Professional antigen presentation (dendritic cells, macrophages, B cells)

**Message**: "This is what I found in my environment." Triggers CD4+ help for B cells and CD8+ T cells.

## Context-Dependent Activation

### Signal 1: Specificity
TCR recognizes peptide-MHC complex:
- **Binding affinity**: Higher affinity → stronger signal
- **Peptide identity**: Determines which T cell clones respond
- **MHC restriction**: T cells only recognize antigen on self-MHC (learned during thymic selection)

Signal 1 alone → **Anergy or tolerance**

### Signal 2: Costimulation
Professional APCs upregulate costimulatory molecules:
- **B7 (CD80/CD86)** on APC → **CD28** on T cell (activating)
- **CTLA-4** on T cell → **B7** on APC (inhibitory, competes with CD28)
- **PD-L1** on APC → **PD-1** on T cell (inhibitory checkpoint)

Signal 1 + Signal 2 → **Activation**

Signal 1 + Inhibitory signals → **Tolerance/Exhaustion**

### Signal 3: Polarization
Cytokine environment determines T cell differentiation:
- **IL-12** → Th1 (cellular immunity, intracellular pathogens)
- **IL-4** → Th2 (humoral immunity, extracellular parasites)
- **TGF-β + IL-6** → Th17 (mucosal immunity, extracellular bacteria)
- **TGF-β alone** → Treg (suppression, tolerance)

Same peptide-MHC → different T cell fates depending on cytokine context.

## Cross-Presentation

**Problem**: CD8+ T cells need to recognize intracellular infections, but they only activate when antigen is presented by professional APCs.

**Solution**: Dendritic cells perform **cross-presentation**:
- Engulf infected/dying cells (extracellular source)
- Shunt antigens into MHC I pathway (normally intracellular route)
- Present on MHC I to activate CD8+ T cells

This allows immune system to detect infections in non-APCs.

## Antigen Processing Pathways

### MHC I Pathway (Endogenous)
1. Proteins degraded by proteasome (cytosol)
2. Peptides transported into ER via TAP transporter
3. Peptides loaded onto MHC I (8-10 amino acids)
4. MHC I trafficked to cell surface

**Surveils**: Viral infection, cancer, cellular health

### MHC II Pathway (Exogenous)
1. Extracellular proteins endocytosed into vesicles
2. Proteins degraded in acidic endosomes/lysosomes
3. MHC II transported to endosomes
4. Peptides loaded onto MHC II (12-25 amino acids)
5. MHC II trafficked to cell surface

**Surveils**: Extracellular pathogens, environmental antigens

## Immunological Synapse

Physical interface between APC and T cell:
- **Central supramolecular activation cluster (cSMAC)**: TCR-MHC complexes cluster
- **Peripheral SMAC (pSMAC)**: Adhesion molecules (LFA-1, ICAM-1)
- **Distal SMAC (dSMAC)**: Large molecules excluded

This is **spatial organization for signal integration**—the synapse is a computational structure.

## MHC Diversity and Transplant Rejection

**HLA (Human Leukocyte Antigen)**: Human MHC genes, extremely polymorphic
- **Purpose**: Population-level diversity ensures some individuals can present any pathogen
- **Consequence**: Transplanted organs express non-self MHC → T cell activation → rejection

**Transplant matching**: Minimize HLA mismatch to reduce rejection risk.

## Context Integration Perspective

Antigen presentation is **multi-input logic gate**:
- **Input 1**: Peptide identity (specificity)
- **Input 2**: MHC type (self-restriction)
- **Input 3**: Costimulation (danger context)
- **Input 4**: Cytokines (polarization signals)

**Output**: T cell fate (activate, tolerate, differentiate)

Same peptide → opposite outcomes depending on context. This is **context conditionality** at molecular scale.

## Related Concepts
- [[Self-Nonself Discrimination]] - MHC-restricted recognition enforces self-MHC learning
- [[Immune Tolerance]] - Lack of costimulation induces tolerance
- [[Danger Theory]] - Costimulation reflects danger signals
- [[Context Conditionality]] - Same antigen, different outcome in different contexts
- [[Immune Checkpoints]] - CTLA-4, PD-1 regulate costimulation
- [[Tumor Immune Evasion]] - Tumors downregulate MHC, avoid presentation
- [[Maternal-Fetal Tolerance]] - Fetus expresses HLA-G (non-classical MHC) to avoid rejection
- [[Clonal Selection Theory]] - Antigen presentation triggers clonal selection

## Tags
#immune-system #antigen-presentation #MHC #HLA #T-cells #costimulation #context #immunological-synapse #cross-presentation
