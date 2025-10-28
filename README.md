# Generational Memory Ontology (GMOnt)

**A lightweight OWL ontology** for representing **family trees**, **generational cohorts**, and **multimodal memories** — including *text*, *audio*, *photo*, and *video*.

---

## Overview

The **Generational Memory Ontology (GMOnt)** provides a minimal yet expressive framework for modeling intergenerational relationships and the cultural artifacts that preserve family memory.  
It is designed for **simplicity**, **interoperability**, and **modular extension**.

---

## Key Features

- **Atomic kinship semantics** — defines only the essential relationships:  
  `parentOf`, `childOf`, `siblingOf`, and `spouseOf`, ensuring clarity and avoiding redundancy.  
- **Media-aware memory modeling** — integrates with [Schema.org](https://schema.org) and [Dublin Core](https://dublincore.org/) to describe *text*, *photo*, *audio*, and *video* artifacts.  
- **Extensible architecture** — SHACL shapes and SPARQL inference/query rules are maintained in companion files for validation, reasoning, and analytic enrichment.  
- **Interoperable** — aligned with FOAF and Schema.org vocabularies for compatibility with broader linked-data ecosystems.  

---

## Repository Structure

```text
ontology/
   generational-memory.ttl              # Core ontology (this file)
   generational-memory.shacl.ttl        # SHACL validation shapes
   generational-memory-all.sparql       # Inference + query rules
samples/
   example.ttl                # Demonstration dataset
README.md
LICENSE
