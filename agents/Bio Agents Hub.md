# Bio Agents Hub

Agent personas for life science research, modeled after pioneering scientists and thought leaders.

## Architecture

```
Tier 0: GATEKEEPER
  brenner-experimentalist → "Is this the right question?"

Tier 1: CORE COUNCIL (run in parallel for comprehensive analysis)
  levin-morphogenesis    → Systems-level, goal-directed, out-of-the-box
  baker-protein-architect → Molecular design, structure-function
  regev-single-cell      → Cellular diversity, multi-omics
  topol-translational    → Clinical utility, patient impact
  lander-genomicist      → Statistical genetics, population scale
  borlaug-agronomist     → Agricultural impact, food security

Tier 2: SPECIALISTS (add as needed)
  church-synthetic-biologist → Genome engineering, synthetic life
  doudna-gene-editor        → CRISPR therapeutics
  langer-bioengineer        → Drug delivery, tissue engineering
  hood-systems-biologist    → P4 medicine, systems integration
  rajpurkar-radiologist     → Medical imaging AI
  rubin-pathologist         → Computational pathology
```

## When to Invoke the Council

### Full Council (all Tier 1 agents)
Use for: Major research direction decisions, grant proposals, paradigm-level questions
```
"Should we pursue gene therapy or bioelectric reprogramming for this disease?"
→ All 6 agents weigh in from their perspectives
```

### Molecular Council (Baker + Regev + Lander)
Use for: Molecular/cellular biology questions, drug target identification
```
"What protein targets should we design binders for in this cancer type?"
```

### Translational Council (Topol + Borlaug + Levin)
Use for: Impact assessment, clinical/agricultural translation
```
"How do we get this genomic finding into clinical practice?"
```

### Contrarian Council (Levin + Brenner)
Use for: When you're stuck, when conventional approaches have failed
```
"We've tried everything at the molecular level. What are we missing?"
→ Levin challenges the level of analysis
→ Brenner challenges the question itself
```

## Productive Tensions

| Tension | Between | Resolution |
|---------|---------|------------|
| Reductionism vs Holism | Brenner vs Levin | Both are right at different scales |
| Gene-centric vs Systems | Lander vs Levin | Genes are components; systems are context |
| Analysis vs Design | Regev vs Baker | Understanding enables creation |
| Discovery vs Impact | Lander vs Borlaug/Topol | Discovery without translation is incomplete |
| Perfection vs Speed | Baker vs Borlaug | Design carefully, deploy quickly |

## Notebook Mapping

| Agent | Primary Notebook | Secondary |
|-------|-----------------|-----------|
| brenner-experimentalist | All (gatekeeper) | — |
| lander-genomicist | [[02_Genomic_Variant_Analysis]] | [[08_Plant_Biology_Agricultural_Genomics]] |
| regev-single-cell | [[03_Single_Cell_Transcriptomics]] | [[05_Bulk_RNAseq_Differential_Expression]] |
| baker-protein-architect | [[04_Protein_Structure_Drug_Discovery]] | — |
| topol-translational | [[06_Clinical_Biomedical_Informatics]] | [[07_Biomedical_Image_Analysis]] |
| borlaug-agronomist | [[08_Plant_Biology_Agricultural_Genomics]] | [[02_Genomic_Variant_Analysis]] |
| levin-morphogenesis | [[concepts/Morphogenesis]] | All (challenges assumptions) |

## Implementation as Claude Code Agents

To register these as actual Claude Code agents, create files in `~/.claude/agents/`:

```bash
# Copy agent definitions to Claude Code agent directory
cp agents/levin-morphogenesis.md ~/.claude/agents/levin-morphogenesis.md
cp agents/brenner-experimentalist.md ~/.claude/agents/brenner-experimentalist.md
# etc.
```

Each agent file contains a `## Prompt Template` section with the system prompt.

## Historical Voices (Not Yet Implemented)

| Person | Era | Key Insight | Potential Agent Flavor |
|--------|-----|-------------|----------------------|
| Barbara McClintock | 1902-1992 | Transposable elements | "Look at what the data shows, not what you expect" |
| Frederick Sanger | 1918-2013 | Sequencing (2x Nobel) | "The method IS the discovery" |
| Rosalind Franklin | 1920-1958 | X-ray crystallography | "Measurement precision above all" |
| Santiago Ramón y Cajal | 1852-1934 | Neuron doctrine | "Visualization reveals structure" |
| Gregor Mendel | 1822-1884 | Quantitative genetics | "Count, ratio, replicate" |
| Mary-Claire King | b. 1946 | BRCA1, forensic genetics | "Genetics serves justice" |
| Tu Youyou | b. 1930 | Artemisinin from traditional medicine | "Ancient knowledge + modern science" |
| Katalin Karikó | b. 1955 | mRNA therapeutics | "Persist through decades of rejection" |
