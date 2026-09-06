# Generational Memory Ontology (GMOnt)

[![Validation](https://github.com/matinabtahi/Generational-MemoryOntology/actions/workflows/validate.yml/badge.svg)](https://github.com/matinabtahi/Generational-MemoryOntology/actions/workflows/validate.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Ontology version](https://img.shields.io/badge/ontology-v1.0.0-blue.svg)](GMOnt.ttl)

**GMOnt** is a lightweight OWL ontology for **longitudinal multimodal archives**: collections in which records about persistent entities are linked across time, generations, lifecycle stages, versions and media formats such as text, images, audio, video, scans, models and datasets.

The ontology is deliberately **domain-general**. It can support family and cultural-memory archives, research collections, institutional records, asset histories, digital heritage and other longitudinal archives without embedding application-specific classes in the core vocabulary.

> **Current version:** GMOnt v1.0.0

## Design idea

GMOnt separates three layers that are often conflated:

1. **Persistent entities** — people, organisations, places, physical/conceptual objects and events.
2. **Archival records** — observations, descriptions, memories or documentary records created at particular times.
3. **Media objects** — the digital files or representations carrying those records, potentially in different formats.

This separation makes it possible to connect heterogeneous records to the same persistent subject while preserving chronology, provenance and media-level relationships.

## Core capabilities

- represent generic `ArchivalRecord` instances and human-centred `Memory` records;
- link records to persistent `Entity` subjects;
- distinguish people, organisations, places, objects and events;
- associate one record with multiple media representations;
- connect records through `previousRecord`, `nextRecord`, `relatedRecord` and `sameSubjectAs`;
- capture derivation between media representations;
- represent generations, cohorts or lifecycle stages without requiring a familial interpretation;
- optionally model kinship and general social relationships;
- align archival records/media with PROV-O and Schema.org concepts.

## Repository layout

```text
.
├── GMOnt.ttl                    # Core ontology (v1.0.0)
├── shapes/
│   └── GMOnt.shacl.ttl          # Lightweight integrity constraints
├── examples/
│   ├── README.md
│   ├── family-memory.ttl        # Human/family-memory example
│   └── building-lifecycle.ttl   # Longitudinal building-lifecycle example
├── queries/
│   ├── README.md
│   ├── next-record.rq
│   ├── same-subject.rq
│   ├── records-by-entity.rq
│   ├── multimodal-records.rq
│   └── ancestor-inference.rq
├── .github/workflows/
│   └── validate.yml
├── CITATION.cff
├── .zenodo.json
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
└── requirements.txt
```

## Quick start

Clone the repository:

```bash
git clone https://github.com/matinabtahi/Generational-MemoryOntology.git
cd Generational-MemoryOntology
```

Install validation dependencies:

```bash
python -m pip install -r requirements.txt
```

Parse the ontology:

```bash
python - <<'PY'
from rdflib import Graph

g = Graph()
g.parse("GMOnt.ttl", format="turtle")
print(f"Loaded {len(g)} RDF triples")
PY
```

Validate an example with SHACL:

```bash
pyshacl -s shapes/GMOnt.shacl.ttl -e GMOnt.ttl examples/building-lifecycle.ttl
```

## Building-lifecycle example

The core ontology contains **no building-specific classes**. [`examples/building-lifecycle.ttl`](examples/building-lifecycle.ttl) shows how the generic model can represent one persistent building across:

- design;
- construction;
- retrofit; and
- post-retrofit operation.

The example links heterogeneous records including a text design narrative, construction photograph, retrofit PDF, scanned drawing, inspection video and IFC building model. All records remain connected to the same persistent building entity while preserving temporal sequence and media relationships.

This makes the example representative of a general **longitudinal multimodal archive**, rather than making the ontology itself building-specific.

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

In GMOnt, *generation* is broader than biological generation. It can denote a cohort, stage, edition or lifecycle phase. Human genealogy remains a supported application, while technical and cultural archives can use the same pattern for successive generations of records, objects or states.

## Namespace

The canonical GMOnt namespace is:

```text
https://matinabtahi.github.io/Generational-MemoryOntology/GMOnt#
```

The source repository is:

```text
https://github.com/matinabtahi/Generational-MemoryOntology
```

The namespace is intended to remain stable across future releases.

## Validation and queries

Automated checks run on every push and pull request:

1. parse all Turtle files with RDFLib;
2. validate both example datasets against the SHACL shapes; and
3. parse every SPARQL query file.

The query catalogue is deliberately split into **one executable query per `.rq` file**, so each query can be run directly rather than being embedded in a multi-query text document.

See [`queries/README.md`](queries/README.md) for the catalogue.

## Citation

GitHub reads citation metadata from [`CITATION.cff`](CITATION.cff). Zenodo-specific release metadata is stored in [`.zenodo.json`](.zenodo.json).

Once a tagged release is archived in Zenodo, cite the version-specific DOI for reproducible scholarly use.

## Contributing

Contributions that improve interoperability, modelling clarity, validation or examples are welcome. See [`CONTRIBUTING.md`](CONTRIBUTING.md).

## License

GMOnt and its examples, shapes and queries are released under the [MIT License](LICENSE).

## Author

**Matin Abtahi**  
Concordia University, Montréal, Canada  
ORCID: [0000-0003-3941-9485](https://orcid.org/0000-0003-3941-9485)
