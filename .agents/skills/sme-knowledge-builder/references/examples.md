# Examples Only: Domain-Agnostic Derivation

These examples demonstrate input-driven derivation. They are not default package targets.

Examples use two confidence fields:

- Input Mapping Confidence: confidence that the package belongs to the SME based on generated inputs.
- Technical Source Confidence: confidence that technical content is substantiated by real gathered or uploaded sources. If sources are only placeholders, use `placeholder`, `not gathered`, or `low`.

## CNC Machining Example

Input signals:

- SME shell role: "Mill-turn cell SME"
- Machines: named mill-turn center and bar feeder
- Materials: stainless and aluminum families
- Responsibilities: first-article support and tool wear interpretation

Possible packages:

- `mill-turn-machining`: process-family or process-subtype package if named in input
- `bar-feeding-systems`: equipment-family package if the feeder scope matters
- `stainless-machining-behavior`: material-family package if material behavior affects SME answers
- `<named-machine-model>`: machine-model package only if the model is named and sourceable

Mapping example:

- Primary Packages: `mill-turn-machining` with Input Mapping Confidence `high`; Technical Source Confidence `placeholder` if no real external or uploaded sources were gathered.
- Context Packages: `<inspection-method>` only if inspection handoff or first-article interpretation appears in the input. This does not expand the machining SME into inspection ownership.

## Injection Molding Example

Input signals:

- SME shell role: "Molding process SME"
- Work center: press group
- Materials: glass-filled thermoplastic
- Responsibilities: setup support, cosmetic defects, dimensional drift

Possible packages:

- `injection-molding`: process-family package if named in input
- `thermoplastic-material-behavior`: material-family package if supported
- `mold-temperature-control`: controls or equipment support package if input names temperature control scope
- `<press-model>`: machine-model package only if named and sourceable

Mapping example:

- Primary Packages: `injection-molding` with Input Mapping Confidence `high`; Technical Source Confidence based only on gathered supplier/OEM/standards sources, or `placeholder` if none were gathered.
- Context Packages: `<inspection-method>` or `<material-family>` only when the input creates a handoff or interpretation need. Context packages provide background, not ownership.

## Heat Treat Or Welding Example

Input signals:

- SME shell role: "Thermal process SME" or "Welding process SME"
- Equipment: furnace, oven, welder, positioner, or monitoring system
- Responsibilities: thermal cycle interpretation, weld quality support, hardness or visual inspection

Possible packages:

- `<named-process-family>`: process-family package derived from the actual input term
- `<named-equipment-family>`: equipment-family package when equipment scope is clear
- `<inspection-method>`: inspection-or-test-method package when inspection responsibility is explicit
- `<controls-topic>`: controls/software/settings package when recipes, programs, or monitoring data are in scope

Do not create these packages unless comparable terms appear in the actual SME inputs.

Mapping example:

- Primary Packages: `<named-process-family>` with Input Mapping Confidence `high` when directly owned by the SME.
- Context Packages: `<inspection-method>` when the SME needs to interpret verification results but does not own final inspection authority.
- Technical Source Confidence remains `placeholder`, `not gathered`, or `low` unless real sources were actually gathered.
