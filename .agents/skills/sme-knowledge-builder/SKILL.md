---
name: sme-knowledge-builder
description: Build and map reusable technical knowledge packages onto generated manufacturing SME shells from sme-registry.md and smes/*.md. Use when creating public-source or uploaded-document knowledge packages for manufacturing SMEs. Do not use for RCCA, evidence requests, troubleshooting checklists, corrective actions, or shop acceptance decisions.
---

# SME Knowledge Builder

## Purpose

Build Layer 4 knowledge packages for a manufacturing SME architecture. Read generated SME shells and create reusable technical knowledge packages plus a map that attaches those packages to SMEs.

Keep the skill manufacturing-domain agnostic. Never hardcode a manufacturing domain into default output. Never create default reflow, SMT, electronics, CCA, machining, molding, welding, heat treat, assembly, packaging, inspection, or other process package folders unless the input files justify those package targets. Treat examples in references as illustrative only.

## Inputs

Locate the repository root or working folder, then discover inputs:

- Required: `sme-registry.md` and/or `smes/*.md`
- Optional: `shop-reference.md`
- Optional later: user-uploaded manuals, work instructions, process specs, inspection criteria, maintenance procedures, and actual records/logs

If neither `sme-registry.md` nor `smes/*.md` exists, stop and ask for the generated SME inputs.

## Outputs

Create or update these Layer 4 outputs:

- `knowledge-package-registry.md`
- `sme-knowledge-map.md`
- `knowledge-packages/<package-name>/knowledge-pack.md`
- `knowledge-packages/<package-name>/source-map.md`

For v0.1, prefer `sme-knowledge-map.md` over editing SME files directly. Do not modify generated SME shells unless the user explicitly requests that. Do not modify the SME Manager.

## Workflow

1. Read `references/package-derivation-rules.md`.
2. Read `sme-registry.md`, then all relevant `smes/*.md`; read `shop-reference.md` if present.
3. Extract SME name, role, owned process or capability, machines, model names, work centers, materials, product or process families, inspection or test responsibilities, and explicit limitations.
4. Derive package targets only from the input content. Use the hierarchy in `package-derivation-rules.md`.
5. Read `references/source-tiering-rules.md` before gathering or classifying sources.
6. Run a targeted source discovery pass for each sourceable package candidate. Use exact machine/model names, equipment-family terms, process-family terms, material terms, and inspection/test method terms from the SME inputs. Prefer OEM, standards, supplier, university, textbook/handbook, and reputable technical sources.
7. Separate input mapping confidence from technical source confidence everywhere. A package can be high-confidence for SME fit while still having placeholder, not gathered, or low technical source confidence.
8. Create shared packages first; avoid one giant package per SME.
9. Split generic process knowledge, equipment-family knowledge, machine-model knowledge, inspection-method knowledge, material-family knowledge, and shop-specific facts when their source support differs.
10. Write `knowledge-package-registry.md` using `references/registry-template.md`.
11. Write `sme-knowledge-map.md` using `references/sme-knowledge-map-template.md`, splitting primary packages from context packages.
12. Write each package folder with `knowledge-pack.md` from `references/knowledge-package-template.md` and a matching `source-map.md`.
13. Validate the result with `references/validation-rules.md`.

## Source Priority

For v0.1, prioritize sources in this order:

1. Generated SME shell
2. `sme-registry.md`
3. `shop-reference.md`, if present
4. Public OEM or general manufacturing knowledge
5. Anecdotal public knowledge, only when clearly labeled

Public web knowledge must never be treated as shop-approved instruction. Public sources can strengthen general understanding, but cannot prove actual shop settings, recipes, acceptance criteria, root cause, or corrective action.

Do not skip public-source research when network access and the task context permit it. If source gathering is blocked by network or permissions, state that in the source map and validation report. If source gathering is possible but a specific package has no credible sources, leave Technical Source Confidence as `placeholder`, `not gathered`, or `low` and explain why.

If public sources were not actually gathered, set Technical Source Confidence to `placeholder`, `not gathered`, or `low`. Do not imply medium or high technical source confidence from public-source placeholders.

## Required Boundaries

This skill is not:

- An RCCA tool
- An evidence-request generator
- A troubleshooting checklist generator
- A corrective-action generator
- An accept/reject decision tool
- A replacement for machine manuals
- A replacement for work instructions
- A replacement for specs, drawings, quality authority, or build records

Write packages as "what a smart manufacturing, process, or equipment SME would know." Do not write them as mandatory evidence checklists or shop disposition instructions.

## Reference Files

- Read `references/package-derivation-rules.md` when deciding package targets.
- Read `references/source-tiering-rules.md` when classifying sources and confidence.
- Read `references/source-tiering-rules.md` before searching so package-specific search queries follow the research strategy.
- Read `references/knowledge-package-template.md` before writing `knowledge-pack.md`.
- Read `references/sme-knowledge-map-template.md` before writing `sme-knowledge-map.md`.
- Read `references/registry-template.md` before writing `knowledge-package-registry.md`.
- Read `references/boundaries-and-overclaiming-rules.md` before making claims from public or generated sources.
- Read `references/validation-rules.md` before finishing.

## Future Layer 5 Direction

Document uploaded-document upgrade opportunities, but do not implement full Layer 5 behavior unless the user explicitly asks. Future source priority should be:

1. Actual build evidence/logs
2. User-uploaded shop documents
3. User-uploaded machine manuals/specs
4. Generated `shop-reference.md` and SME shells
5. Public/OEM/general knowledge packages
6. Anecdotal tricks/forums/videos
