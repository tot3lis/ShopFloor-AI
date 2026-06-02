# Package Derivation Rules

Use these rules to derive package targets from generated SME shells and registries. Do not seed package names from outside the inputs.

## Extraction

From `sme-registry.md`, `smes/*.md`, and optional `shop-reference.md`, extract:

- SME name
- SME role
- Owned process or capability
- Machine names
- Machine model names
- Work centers
- Materials
- Product families or process families
- Inspection or test responsibilities
- Controls, software, recipes, programs, settings, or data systems
- Explicit limitations and uncertainty statements

Normalize names conservatively. Preserve original names in notes when normalization could lose meaning.

## Package Hierarchy

Derive package targets using this stacked hierarchy:

1. `domain-general`: broad manufacturing, quality, production, maintenance, safety, metrology, or engineering concepts directly implied by the SME set.
2. `process-family`: broad process categories explicitly named or directly inferred from SME-owned capabilities.
3. `process-subtype`: narrower process forms named in SME content.
4. `equipment-family`: equipment classes named or clearly implied by machines, work centers, or roles.
5. `machine-model`: only when a named machine or model is present and reliable public or uploaded sources can support useful details.
6. `material-family`: when materials are named and materially affect process knowledge.
7. `inspection-or-test-method`: when inspection or test methods are named or assigned to an SME.
8. `controls-software-settings`: when controls, programs, recipes, parameters, software, data systems, or machine settings are part of the SME scope.

Create a package only when it has a clear reason to exist and enough input support to write useful, bounded technical context. Keep source coverage separate from input support.

## Sourceable Package Decision

After deriving candidate packages, decide whether each package is sourceable:

- Always source process-family, process-subtype, equipment-family, material-family, and inspection/test-method packages when credible public or uploaded sources are available.
- Create machine-model packages when the SME inputs name a machine/model and at least one credible OEM, vendor, distributor, manual, datasheet, or uploaded source gives useful model-specific context.
- Do not create a machine-model package from general process knowledge alone. If no credible model source is found, keep the topic as an equipment-family or process package and list the model-specific package as deferred.
- Do not collapse sourceable machine-model content into a generic process package when the source level, limits, or ownership differs.
- Do not create a package that only repeats the SME shell; the package must add technical principles, mechanisms, variables, terminology, or source-backed context.

## Sharing Rules

Prefer shared packages that multiple SMEs can use. Split packages when:

- One package would mix unrelated capabilities.
- Different source tiers or confidence levels need different boundaries.
- A machine-model package depends on sources that should not be implied for a whole equipment family.
- A material, inspection method, or controls topic cuts across multiple process packages.

Merge packages when:

- Two candidate packages have the same scope and sources.
- One package would contain only thin restatement of an SME shell.
- A subtype is not sourceable beyond the parent process family.

Do not merge when:

- One package is general process knowledge and another is model-specific public/OEM knowledge.
- One package is shop-specific generated context and another is public/generic technical context.
- One package has medium/high technical source confidence and another remains placeholder or low.

## Naming

Use lowercase hyphen-case folder names. Prefer names that describe scope:

- `<domain-general>`
- `<process-family>`
- `<process-subtype>`
- `<equipment-family>`
- `<machine-model-if-sourceable>`
- `<material-family>`
- `<inspection-or-test-method>`
- `<controls-or-software-topic>`

Do not use domain-specific names unless the input files contain or directly imply that domain. Examples in this skill are not candidate package names.

## Confidence Model

Use two confidence fields everywhere.

### Input Mapping Confidence

Confidence that the package belongs to an SME based on `sme-registry.md`, `smes/*.md`, and optional `shop-reference.md`.

- High: SME scope explicitly names the package topic, process, equipment family, material, method, or responsibility.
- Medium: SME scope strongly implies the package topic through work center, product flow, adjacent responsibility, or shared inspection/handoff context.
- Low: SME fit is plausible but indirect, partial, or uncertain.

### Technical Source Confidence

Confidence that the package's technical content is substantiated by real external or uploaded sources, such as OEM docs, standards, supplier docs, academic references, trade publications, user manuals, work instructions, specs, or actual records.

- High: real, relevant Tier 1-2 or uploaded/actual sources directly support the technical content.
- Medium: real, relevant Tier 3-5 sources support the general technical content, but machine/shop specificity is limited.
- Low: sources are sparse, indirect, anecdotal, or only broadly relevant.
- Placeholder or not gathered: no real public, external, uploaded, or actual-record sources were gathered.

If public sources were not actually gathered, Technical Source Confidence must be `placeholder`, `not gathered`, or `low`. A public-source placeholder may support package scaffolding, but it does not substantiate technical claims as real cited evidence.

When in doubt, create a missing package opportunity in `sme-knowledge-map.md` instead of creating a weak package.

## Required Package Depth

For each created package, include technical substance that matches the package scope:

- process principles
- equipment or tooling principles
- important variables and their directionally relevant effects
- process-window or measurement-window concepts
- material, geometry, environment, and operator interactions
- common failure modes
- physical, procedural, thermal, mechanical, dimensional, material, or software failure mechanisms
- practical heuristics clearly bounded by source confidence
- terminology SMEs and routers can reuse

Avoid filler. If a section cannot be supported by sources, state the limitation and list the needed source.
