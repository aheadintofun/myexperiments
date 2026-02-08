# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a bioinformatics knowledge collection within an Obsidian vault. It contains curated notes on AI-powered structural biology tools, open data resources, and systems biology concepts for building analytical platforms.

## Content Structure

**Shiny Objects (Yearly Toolkits)**
- `2024 Shiny objects.md` - Mature tools: AlphaFold 2, ProteinMPNN, RFdiffusion, ESM-2, DiffDock
- `2025 Shiny objects.md` - Open weights revolution: Chai-1, Boltz-1, ESM3, OpenCRISPR-1
- `2026 Shiny objects.md` - Foundation models: AlphaGenome, Evo 2, AlphaFold 3, scGPT

**Resources**
- `Accessible Data.md` - Open data repositories (NCBI, EMBL-EBI, CellxGene, cloud datasets)
- `AI Bio Scientists.md` - AI-powered biology platforms and services

**Conceptual Frameworks**
- `Vibing w Opus 4.6.md` - Full-stack scientific computing architecture; universal biological abstractions (trajectories, hierarchical composition, perturbation-response, degeneracy, context-conditionality)
- `Cache and Lattes.md` - Cellular automata frameworks for modeling biological/social systems; cachexia as phase transition; hormesis and regenerative inversions

## Conventions

- Notes use Markdown with Obsidian-style `[[wikilinks]]`
- Tool matrices use `🟢/🟡/🔴` for Mac M4 vs Cloud compatibility ratings
- Code snippets target Mac M4 (32GB) with MPS acceleration or Google Colab
- LaTeX math via `$$formula$$` when needed

## Key Themes

The collection explores a unifying view of biology as multi-scale algebraic systems:
- **Trajectory engines** - differentiation, disease progression, crop maturation
- **Hierarchical composition** - molecule → cell → tissue → organism → population
- **Perturbation-response** - drugs, CRISPR, environmental stress
- **Degeneracy** - many-to-many mappings (genotype-phenotype, drug-effect)
- **Context-conditionality** - f(genotype, context) → phenotype_distribution

## Tool Implementation Notes

**Local Mac M4 (32GB)**
- scGPT, ESM-2, ProteinMPNN, LocalColabFold, Boltz-1 run well
- Use `torch.device("mps")` for Apple GPU acceleration

**Cloud Required**
- RFdiffusion (CUDA-dependent)
- AlphaFold 3 (Linux/CUDA specific)
- AlphaGenome (API-based, compute on Google Cloud)
