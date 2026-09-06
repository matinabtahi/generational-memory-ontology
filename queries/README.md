# GMOnt SPARQL queries

Each `.rq` file contains **one executable SPARQL query**.

| Query | Purpose |
|---|---|
| `next-record.rq` | Materialize `nextRecord` from explicit `previousRecord` links |
| `same-subject.rq` | Construct `sameSubjectAs` links for records sharing a subject |
| `records-by-entity.rq` | Retrieve a chronological record sequence for one entity |
| `multimodal-records.rq` | Retrieve media representations grouped by entity and date |
| `ancestor-inference.rq` | Human/family specialization: infer `ancestorOf` from parent paths |

For `records-by-entity.rq`, bind the `?entity` variable in your SPARQL client or replace it with a concrete IRI before execution.

The subject-oriented queries explicitly include GMOnt's specialized `about*` properties, so they work on the example data without requiring a separate RDFS inference step.
