# Foundation Models in Biology

## Definition
Large-scale neural networks trained on broad biological data (genomes, proteomes, cells, tissues) that learn general-purpose representations transferable to diverse downstream tasks. Analogous to GPT/BERT in natural language—pre-trained on unlabeled data, then fine-tuned for specific applications.

## Computational Structure
The general paradigm:
$$\text{Raw Data} \xrightarrow{\text{self-supervised pre-training}} \text{Foundation Model} \xrightarrow{\text{fine-tuning}} \text{Task-Specific Model}$$

**Key property**: Zero-shot or few-shot performance on new tasks without retraining from scratch.

## Foundation Model Hierarchy (2024-2026)

### Protein Scale
**ESM-2/ESM3** (EvolutionaryScale)
- Training: 65M-15B parameters on UniRef (protein sequences)
- Representation: Amino acid embeddings capturing evolution + structure
- Tasks: Function prediction, stability, variant effects

### Genome Scale
**AlphaGenome** (DeepMind, 2026)
- Training: 1M nucleotide context window on human genome + epigenetics
- Representation: DNA sequence → chromatin state predictions
- Tasks: Variant effect prediction, regulatory element discovery

**Evo** (Arc Institute, 2025)
- Training: 131k nucleotide context, trained on bacteria and phages
- Representation: Generative DNA model
- Tasks: Design CRISPR systems, synthetic viral vectors

### Cell Scale
**scGPT** (University of Toronto, 2024)
- Training: 10M+ single cells from atlases (Tabula Sapiens, CellxGene)
- Representation: Gene expression profiles → cell state embeddings
- Tasks: Cell type annotation, gene knockout prediction, trajectory inference

**Geneformer** (Theodoris Lab, 2023)
- Training: Self-supervised on ranked gene expression
- Representation: Context-aware gene embeddings
- Tasks: In silico perturbations, dosage sensitivity

### Tissue Scale
**H-Optimus-0** (Bioptimus, 2025)
- Training: 1B+ histopathology image patches from diverse tissues
- Representation: Vision transformer on H&E slides
- Tasks: Gene expression from images, tumor classification, prognosis

### Multi-Modal
**AlphaFold 3** (DeepMind, 2024)
- Training: Protein sequences + structures + small molecules + nucleic acids
- Representation: Unified embedding space for all molecular types
- Tasks: Structure prediction, docking, complex assembly

**Chai-1** (Chai Discovery, 2024)
- Training: Similar to AF3 but fully open weights
- Representation: Multi-modal molecular embeddings
- Tasks: Protein-drug interactions, RNA-protein binding

## Key Characteristics

### Scale
Foundation models require massive data and compute:
- **ESM-2**: 65M-15B parameters, trained on 200M sequences
- **AlphaGenome**: 1M bp context (50x larger than prior genomic models)
- **H-Optimus-0**: 1.1B parameters, trained on 500k+ slides
- **scGPT**: 10M cells (entire human cell atlas)

### Transfer Learning
Pre-trained representations enable few-shot learning:
- **Example**: scGPT trained on healthy cells can predict cancer cell states with <100 labeled examples
- **Example**: ESM-2 predicts enzyme function with zero task-specific training

### Emergent Capabilities
Behaviors not explicitly trained:
- **ESM3**: Generates functional GFP variants never seen in training
- **AlphaGenome**: Predicts long-range chromatin interactions from sequence alone
- **scGPT**: Simulates gene knockouts for genes with no knockout data

## The Open Weights Movement (2025-2026)
Critical shift: **democratization** of foundation models.

### Closed Source (2024)
- AlphaFold 3: Server-only access, no downloadable weights
- Limitation: Cannot integrate into custom pipelines, API rate limits

### Open Weights (2025-2026)
- Chai-1, Boltz-1: Full model weights released
- ESM3: Small/medium models open, large models API-gated
- scGPT: Fully open, runs on Mac M4
- **Impact**: Academic labs can now deploy foundation models locally

## Key Insight
Foundation models represent **compressed knowledge of biological domains**. They are not merely tools—they are **learned representations of biological reality**. Fine-tuning a foundation model is asking: "What does the model's internal representation predict about my specific problem?"

This is [[Information Compression in Biology]] at the computational scale.

## Hardware Accessibility

### Mac M4 (32GB) Native
- ✅ scGPT (excellent MPS support)
- ✅ ESM-2 (650M parameter models run fast)
- ⚠️ Chai-1 (slow but possible)

### Colab/Cloud Required
- AlphaGenome (API client runs locally, compute remote)
- H-Optimus-0 (1B+ parameters, GPU memory intensive)
- AlphaFold 3 (server-only)

## Related Concepts
- [[Protein Language Models]] - Foundation models for protein sequences
- [[Information Compression in Biology]] - Foundation models compress domain knowledge
- [[Variant-Phenotype Mapping]] - Foundation models predict variant effects
- [[Multi-Omics Integration]] - Multi-modal foundation models integrate data types
- [[Transfer Learning in Biology]] - Fine-tuning foundation models for specific tasks

## Tags
#foundation-models #transfer-learning #deep-learning #embeddings #zero-shot #few-shot #representation-learning #computational-biology #esm #alphafold #scgpt
