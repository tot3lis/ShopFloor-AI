# Router Trigger Rules

Routing triggers are semantic hints for a future SME Answer Router, not strict exact-match rules.

The future router should infer SME relevance from:

- meaning of the user question
- shop context
- synonyms and aliases
- operation relationships
- machine relationships
- upstream/downstream context
- evidence type mentioned

The user should not need to know exact machine names, operation names, work center names, or shop jargon.

Every SME shell must include:

1. Exact / Named Triggers
2. Semantic / Plain-Language Triggers
3. Routing Notes

## Exact / Named Triggers

Include source-specific identifiers such as:

- SME name
- machine name
- machine aliases
- operation numbers
- operation names
- work centers
- named records
- named documents
- named capabilities

## Semantic / Plain-Language Triggers

Include plain-language terms that may imply this SME even when the user does not use exact shop terminology.

For Shop Flow SME, include flow concepts:

- route
- operation
- step
- before
- after
- upstream
- downstream
- sequence
- work center
- where does this happen
- who owns this operation
- what happens next
- what happens before this
- traveler

For Inspection SME, include evidence and acceptance concepts:

- inspection
- check
- verify
- acceptance
- criteria
- defect confirmation
- evidence
- photo
- AOI
- CMM
- visual inspection
- final inspection
- test result
- accept/reject
- workmanship
- drawing
- spec
- before or after

For Machine / Capability SMEs, include terms related to:

- what the machine does
- plain-English process descriptions
- common non-technical wording
- safe evidence words
- associated records or documents
- upstream/downstream process concepts

## Routing Notes

Include when the future router should invoke this SME alongside others.

Examples:

- Invoke with Shop Flow SME when operation sequence or upstream/downstream context matters.
- Invoke with Inspection SME when the question asks what evidence proves detection, acceptance, or before/after condition.
- Invoke with related upstream machine SMEs when the issue may involve earlier process steps.

## Guardrails

- Do not make triggers into exact-match gates.
- Do not add every possible trigger to every shell.
- Keep triggers relevant to the SME and source.
- Do not turn trigger examples into process advice.
