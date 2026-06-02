# Source Depth Rules

Use the lowest source depth that accurately reflects the available evidence.

Level 1 = User-requested shell only:

- SME was requested by the user without supporting `shop-reference.md` evidence.

Level 2 = Public reference supported:

- Public references were explicitly provided or created in a future workflow.
- Do not use Level 2 by default.

Level 3 = Shop-reference supported:

- SME is generated from `shop-reference.md`.
- Default for `Shop Flow SME`.
- Default for `Inspection SME`.
- Default for Machine / Capability SMEs generated from named machines, equipment, stations, cells, benches, or capabilities in `shop-reference.md`.

Level 4 = Internal documentation supported:

- Manuals, work instructions, process specs, acceptance criteria, datasheets, maintenance documents, recipes, procedures, drawings, or shop procedures are provided.

Level 5 = Evidence supported:

- Actual shop evidence is provided, such as logs, inspection records, test results, photos, cure records, machine records, maintenance tickets, or traceability records.

## Guardrails

- Do not claim Level 4 because a document type would be useful later.
- Do not claim Level 5 because the source says records are retained.
- Retained-record statements in `shop-reference.md` remain Level 3 unless the actual records are provided.
