# Machine Context Rules

Use machine context to classify and describe Machine / Capability SMEs.

## Context To Capture

For each named machine/capability, capture:

- exact source name
- type/capability
- work center
- associated operation/process
- product or route scope
- standard, conditional, alternate, optional, backup, inactive, or unknown status
- records/logs named by the source
- useful future uploads such as manuals, specs, work instructions, recipes, maintenance documents, setup records, inspection records, or test records

## Classification Cues

- Standard operation link -> Required.
- Conditional, repair, rework, alternate, special, backup, or when-required link -> Conditional.
- Listed but not tied to provided standard flow -> Optional / Capability Available.
- Unclear support or missing description -> Needs Review.
- Explicitly route context only -> do not create a required SME.

## Generic Names

Generic benches, stations, cells, or labels can become Machine / Capability SMEs if they are assigned to an operation.

If the source says a label is generic, backup-only, inactive, or not an assigned station, lower status/confidence or keep it as route context only.
