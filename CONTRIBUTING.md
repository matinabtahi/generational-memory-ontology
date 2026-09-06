# Contributing to GMOnt

Contributions that improve correctness, interoperability, examples, validation or documentation are welcome.

## Ontology conventions

1. Keep the canonical namespace unchanged:
   `https://matinabtahi.github.io/Generational-MemoryOntology/GMOnt#`
2. Prefer domain-general core terms. Domain-specific concepts belong in examples or extension profiles unless they are broadly reusable.
3. Add an English `rdfs:label` and concise `rdfs:comment` for new public classes and properties.
4. Prefer existing standards such as PROV-O, Schema.org, SKOS and Dublin Core where they already express the required concept.
5. Keep each SPARQL query in a separate `.rq` file.
6. Update the SHACL shapes and examples when a change affects expected data structure.
7. Update `CHANGELOG.md` for user-visible ontology changes.

## Local validation

```bash
python -m pip install -r requirements.txt

python - <<'PY'
from pathlib import Path
from rdflib import Graph
from rdflib.plugins.sparql import prepareQuery

for path in sorted(Path(".").rglob("*.ttl")):
    Graph().parse(path, format="turtle")
    print(f"OK  {path}")

for path in sorted(Path("queries").glob("*.rq")):
    prepareQuery(path.read_text(encoding="utf-8"))
    print(f"OK  {path}")
PY

pyshacl -s shapes/GMOnt.shacl.ttl -e GMOnt.ttl examples/family-memory.ttl
pyshacl -s shapes/GMOnt.shacl.ttl -e GMOnt.ttl examples/building-lifecycle.ttl
```

## Versioning

GMOnt follows semantic versioning:

- **PATCH** — documentation/metadata corrections that do not change ontology semantics;
- **MINOR** — backward-compatible ontology additions;
- **MAJOR** — incompatible semantic changes.

Once a namespace or public term has been released, stability takes precedence over matching future repository naming changes.
