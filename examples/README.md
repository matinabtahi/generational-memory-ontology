# GMOnt examples

The examples are intentionally small and domain-focused while using the same generic GMOnt core.

## `family-memory.ttl`

Demonstrates a human/intergenerational archive with:

- people and family relationships;
- generational cohorts;
- an audio memory record;
- a later video reflection; and
- longitudinal links between records.

## `building-lifecycle.ttl`

Demonstrates a technical longitudinal archive in which one building is tracked across:

- design;
- construction;
- retrofit; and
- post-retrofit operation.

The record sequence includes text, image, PDF, scan, video and IFC media representations.

## Validate both examples

```bash
python -m pip install -r requirements.txt

pyshacl -s shapes/GMOnt.shacl.ttl -e GMOnt.ttl examples/family-memory.ttl
pyshacl -s shapes/GMOnt.shacl.ttl -e GMOnt.ttl examples/building-lifecycle.ttl
```
