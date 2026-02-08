# Knowledge Graph as Biological Substrate

## Definition
The architectural insight: all biological domains reduce to a **knowledge graph problem** with shared computational grammar. Entities, relationships, observations, and inference compose a universal substrate on which domain-specific analyses operate as plugins.

## Graph Structure

### Entities (Nodes)
- Genes, variants, proteins, metabolites
- Cells, tissues, organs, organisms
- Environments, treatments, phenotypes
- Diseases, drugs, pathways

### Relationships (Edges)
- **Causal**: X causes Y, X regulates Y
- **Functional**: X interacts-with Y, X co-expressed-with Y
- **Evolutionary**: X homologous-to Y, X selected-for
- **Spatial**: X adjacent-to Y, X located-in Y
- **Temporal**: X precedes Y, X co-occurs-with Y

### Observations (Attributes)
Multi-modal measurements at varying resolution:
- Bulk measurements (population average)
- Single-cell resolution (cellular heterogeneity)
- Spatial resolution (tissue architecture)
- Temporal resolution (dynamics)
- Subcellular resolution (organellar localization)

### Inference (Graph Queries)
What's the causal chain from perturbation to phenotype?
- Path queries: gene → protein → pathway → phenotype
- Neighborhood queries: what interacts with this target?
- Subgraph queries: disease module in network
- Traversal: how does signal propagate?

## Universal Computational Grammar

The cultivar breeder and oncologist ask structurally identical questions:
> Which variants in which context produce which outcome, and how do I intervene?

This translates to graph queries:
1. **Variant identification**: Nodes with variant attributes
2. **Context specification**: Subgraph induced by context
3. **Outcome prediction**: Path traversal to phenotype nodes
4. **Intervention design**: Identify druggable nodes on causal paths

## Implementation Technologies

### Graph Databases
- **Neo4j**: Property graph database (Cypher query language)
- **RDF/SPARQL**: Semantic web standards, ontology integration
- **TigerGraph**: Distributed graph analytics
- **Amazon Neptune**: Managed graph database

### Ontologies (Structured Vocabularies)
- **Gene Ontology (GO)**: Molecular function, biological process, cellular component
- **Disease Ontology (DO)**: Human disease classification
- **HPO**: Human phenotype ontology (rare disease)
- **Plant Ontology, Crop Ontology**: Agricultural traits
- **ChEBI**: Chemical entities of biological interest
- **Cell Ontology**: Cell type classification

### Knowledge Bases
- **Reactome, KEGG, WikiPathways**: Biological pathways
- **STRING**: Protein-protein interactions
- **COSMIC, ClinVar**: Variant-disease associations
- **Gramene, MaizeGDB**: Plant genomic databases

## Architectural Vision
Instead of isolated domain-specific tools, a unified platform:

1. **Shared knowledge graph** (Neo4j/RDF) stores all biological entities and relationships
2. **Standardized multi-omics objects** (MuData/AnnData) for observations
3. **Domain-specific analysis plugins** write results back to graph
4. **Workflow orchestrator** (Nextflow) chains analyses
5. **ML/foundation models** operate on graph embeddings

## Key Advantages
- **Cross-domain queries**: Find analogous biology in different domains
- **Transfer learning**: Leverage knowledge from one domain in another
- **Causal inference**: Explicit representation of causal relationships
- **Extensibility**: Add new data types as new node/edge attributes
- **Provenance**: Track analytical workflows as graph annotations

## Example: Variant Effect Prediction
Traditional approach:
```
variant → annotation tool → functional prediction → phenotype lookup
```

Graph approach:
```
Cypher query:
MATCH (v:Variant)-[:AFFECTS]->(g:Gene)-[:ENCODES]->(p:Protein)
      -[:PARTICIPATES_IN]->(pw:Pathway)-[:INFLUENCES]->(ph:Phenotype)
WHERE v.id = 'rs12345' AND context.tissue = 'liver'
RETURN ph.name, confidence_score
```

The graph explicitly represents causal chain, enables context-aware queries, supports mechanistic reasoning.

## Related Concepts
- [[Variant-Phenotype Mapping]] - Variant effect graphs
- [[Multi-Omics Integration]] - Observations as graph attributes
- [[Hierarchical Composition]] - Nested subgraphs at each scale
- [[Context Conditionality]] - Context as subgraph selection
- [[Information Compression in Biology]] - Graph embeddings as compression

## Tags
#knowledge-graph #Neo4j #ontology #causal-inference #systems-biology #graph-database #semantic-web #data-integration
