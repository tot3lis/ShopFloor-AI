# Shop-Floor Detection Rules

This reference is retained for compatibility with older prompts. The current architecture does not generate SMEs from every shop-floor task.

Use task and operation detection only to:

- understand shop flow
- map named machines/capabilities to operations
- identify inspection/test/acceptance points for `Inspection SME`
- classify route status for Machine / Capability SMEs
- create open questions when mappings are ambiguous

Do not create separate task/process SMEs by default.

## Primary Detection Targets

Detect:

- named machines
- named equipment assets
- named stations
- named cells
- named benches
- named tooling areas
- major named capabilities
- standard/conditional/alternate route status
- inspection/test/acceptance points

## De-Emphasized Targets

Do not generate separate SMEs by default for:

- kitting
- material issue
- material traceability
- MRB
- rework
- manual assembly
- maintenance
- testing
- broad operation/task clusters

These can still appear inside Shop Flow SME, Inspection SME, or a relevant Machine / Capability SME.

## Guardrails

Do not perform RCCA, root cause analysis, corrective action, SPC analysis, machine performance analysis, process advice, web scraping, or vector DB work.
