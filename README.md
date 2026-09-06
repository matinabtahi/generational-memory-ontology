# Generational Memory Ontology (GMOnt)

**GMOnt** is a lightweight OWL ontology for **longitudinal multimodal archives**: collections in which records about persistent entities must be linked across time, versions and media formats such as text, image, audio, video, scans, models and datasets.

The ontology is deliberately **domain-general**. It can support family and cultural-memory archives, research collections, institutional records, asset histories, digital heritage and other longitudinal archives without embedding application-specific classes in the core vocabulary.

> **Current ontology version:** GMOnt v1.0.0

## Design idea

GMOnt separates three things that are often conflated:

1. **Persistent entities** — people, organisations, places, physical/conceptual objects and events.
2. **Archival records** — observations, descriptions, memories or documentary records created at particular times.
3. **Media objects** — the digital files or representations carrying those records, potentially in different formats.

This separation allows different records and media to remain connected to the same subject over time.

## Core capabilities

- represent generic `ArchivalRecord` instances and human-centred `Memory` records
- link records to persistent `Entity` subjects
- distinguish people, organisations, places, objects and events
- associate one record with multiple media representations
- connect records through `previousRecord`, `nextRecord`, `relatedRecord` and `sameSubjectAs`
- capture derivation between media representations
- represent generations/cohorts without requiring familial interpretation
- optionally model kinship and general social relationships
- retain provenance-friendly alignment with PROV-O and media alignment with Schema.org

## Building-lifecycle example

The core ontology contains **no building-specific classes**. Instead, `examples/building-lifecycle.ttl` demonstrates one application profile relevant to longitudinal building archives.

The example follows a building across several lifecycle stages and links heterogeneous records such as:

- an original design text record
- a construction photograph
- a retrofit report
- a later inspection video
- a digital model/dataset

All of those records remain connected to the same persistent building entity and to one another through temporal and subject relationships. This demonstrates the proposal use case: a lightweight OWL ontology for **longitudinal multimodal archives linking records across time and formats**, applicable to **building-lifecycle digital archives**.

## Repository contents

| File | Purpose |
|---|---|
| `generational-memory.ttl` | Core GMOnt ontology |
| `generational-memory.shacl.ttl` | Lightweight SHACL validation shapes |
| `generational-memory-rules.sparql` | Example SPARQL inference/query patterns |
| `example.ttl` | Human/family-memory example |
| `examples/building-lifecycle.ttl` | Domain-specific demonstration for a building-lifecycle multimodal archive |
| `CITATION.cff` | Citation metadata for GitHub |
| `.zenodo.json` | Zenodo deposition metadata |
| `LICENSE` | MIT licence |

## Canonical namespace

```text
https://matinabtahi.github.io/Generational-Memory-Ontology-GMOnt/GMOnt#
```

## Minimal pattern

```turtle
ex:BuildingA a gmont:Object .

ex:Record2020 a gmont:ArchivalRecord ;
    gmont:aboutObject ex:BuildingA ;
    gmont:recordDate "2020-05-10"^^xsd:date ;
    gmont:hasMedia ex:Photo2020 .

ex:Record2025 a gmont:ArchivalRecord ;
    gmont:aboutObject ex:BuildingA ;
    gmont:recordDate "2025-08-12"^^xsd:date ;
    gmont:previousRecord ex:Record2020 ;
    gmont:sameSubjectAs ex:Record2020 ;
    gmont:hasMedia ex:InspectionVideo2025 .
```

## Why “Generational”?

In GMOnt, *generation* is broader than biological generation. It can denote a cohort, stage, edition or lifecycle phase. Human genealogy remains a supported application, but the ontology can also express successive generations of records, objects or states in technical and cultural archives.

## Citation and archival release

GitHub reads citation metadata from `CITATION.cff`. For scholarly citation, use the version-specific Zenodo DOI once a tagged GitHub release has been archived.

## Licence

GMOnt is released under the **MIT License**.

## Author

**Matin Abtahi**  
Concordia University, Montréal, Canada  
ORCID: 0000-0003-3941-9485
