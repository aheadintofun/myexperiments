# Transfer Learning in Biology

## Definition
Using knowledge learned from one biological domain or task to accelerate learning in a related but different domain. In machine learning for biology, this means pre-training models on large unlabeled datasets, then fine-tuning on specific downstream tasks with limited labeled data.

## Core Mechanism
1. **Pre-training phase**: Model learns general representations from abundant unlabeled data (protein sequences, single-cell profiles, genomic data)
2. **Transfer phase**: Learned representations capture fundamental biological patterns
3. **Fine-tuning phase**: Adapt pre-trained model to specific task with minimal task-specific data

## Biological Analogy
Transfer learning mirrors evolution itself:
- Pre-training = evolutionary history encodes general solutions
- Fine-tuning = adaptive radiation for specific niches
- Representations = conserved molecular machinery repurposed across contexts

## Examples in Computational Biology

### Protein Models
- **ESM-2** pre-trained on 250M sequences → fine-tune for structure prediction, variant effects, binding sites
- **ProteinMPNN** learns sequence-structure relationships → fine-tune for specific protein families

### Single-Cell Models
- **scGPT** pre-trained on 33M cells → fine-tune for cell type annotation, perturbation prediction
- **Geneformer** learns gene regulatory logic → transfer to disease-specific datasets

### Genomics
- **Nucleotide Transformer** pre-trained on genomes → fine-tune for promoter prediction, splice site detection

## Efficiency Gains
Transfer learning provides massive sample efficiency:
- Pre-training: millions-billions of examples (unlabeled)
- Fine-tuning: hundreds-thousands of examples (labeled)
- **Result**: Achieve expert performance with limited labeled data

## Why It Works in Biology
Biology has deep hierarchical structure with conserved principles:
- Same protein folds across kingdoms
- Same gene regulatory motifs across species
- Same cell types across individuals

Pre-training captures these universal patterns. Fine-tuning specializes to context-specific details.

## Related Concepts
- [[Foundation Models in Biology]] - Transfer learning at scale
- [[Protein Language Models]] - Pre-trained models for sequence tasks
- [[Single-Cell Foundation Models]] - Transfer learning for cell biology
- [[Information Compression in Biology]] - Pre-training compresses evolutionary knowledge
- [[Context Conditionality]] - Fine-tuning learns context-specific mappings
- [[Variant Effect Prediction]] - Transfer learning for clinical variant interpretation

#transfer-learning #foundation-models #machine-learning #representation-learning #pre-training
