---
name: sme-generator
description: Generate shop-aware SME coverage from ShopContext shop-reference.md files. Use when the user wants to determine which machine/capability SME modules are needed, create sme-coverage.md, create sme-registry.md, or generate SME profile shells. Do not use for RCCA, root cause analysis, corrective action, defect investigation, SPC analysis, machine performance analysis, or technical process advice.
---

# SME Generator

## 1. What This Skill Does

This skill reads one or more ShopContext `shop-reference.md` files and creates a shop-aware SME coverage layer focused on:

1. Machine / Capability SMEs
2. Shop Flow SME
3. Inspection SME

The skill is reference-driven. It starts from the machine list, equipment list, station/cell references, work center context, and machine-to-operation mappings in `shop-reference.md`. It creates one SME candidate for each named machine, station, cell, equipment asset, or major capability, then uses the standard operation flow to classify whether that SME is Required, Conditional, Optional / Capability Available, or Needs Review.

Always generate:

- `Shop Flow SME`
- `Inspection SME`

This skill creates coverage, registry, and profile shells only. It does not create final SME knowledge packs.

Do not generate separate SMEs for kitting, MRB, manual assembly, material traceability, rework, testing, maintenance, or broad process/task clusters unless they are represented as a named machine/station/capability or the user explicitly requests them.

The Answer Router later decides which SME answers what. Layer 3 knowledge packages later make each machine/capability SME useful by adding manuals, specs, process knowledge, maintenance knowledge, capability details, evidence interpretation, and related documents.

Every generated SME shell must be router-ready. The future SME Answer Router / Orchestrator should be able to read the shell and determine what the SME knows now, when it should be invoked, what it can and cannot answer yet, what records/documents/evidence it needs, what boundaries it must obey, and what contribution it should provide when invoked.

Routing triggers are semantic hints, not strict exact-match rules. The future router should infer relevance from meaning, synonyms, aliases, operation relationships, machine relationships, upstream/downstream context, evidence type, and plain-language user questions. Users should not need exact machine names, operation names, work center names, or shop jargon.

## 2. When To Use This Skill

Use this skill when the user asks to:

- generate SMEs from `shop-reference.md`
- determine which machine/capability SMEs a shop needs
- create SME coverage
- create an SME registry
- create SME profile shells
- add a user-requested SME
- map machines/capabilities to SMEs
- validate SME shell generation from shop references

## 3. When Not To Use This Skill

Do not use this skill for:

- RCCA
- root cause analysis
- corrective action
- defect investigation
- ProblemPath routing
- technical process advice
- SPC analysis
- machine performance analysis
- maintenance event analysis
- data integration
- machine log analysis
- final RCCA writing
- management insight answers
- training answers
- web scraping
- vector database creation

If a user asks a technical or process question, identify the relevant SME or SMEs, but do not answer the process question. State that technical answering belongs to a later SME pack or another skill.

## 4. Required Inputs

Primary input:

- `shop-reference.md`

The skill should work from `shop-reference.md` alone.

## 5. Optional Inputs

Optional inputs:

- additional `shop-reference.md` files
- user-requested SME names
- user notes about missing SMEs
- manual, spec, work-instruction, procedure, maintenance, or evidence references if already present

Do not scrape the web. Do not create public references unless explicitly provided or requested in a future workflow.

## 6. Required Outputs

Generate outputs in the working area where the user requests them, unless the user specifies a target output directory:

- `sme-coverage.md`
- `sme-registry.md`
- `smes/[sme-name].md`

If running inside a repo with project folders, place outputs in a logical project folder and avoid unrelated files.

## 7. Workflow Steps

1. Locate and read `shop-reference.md`.
2. Extract relevant ShopContext sections:
   - Shop Overview
   - Source Documents Reviewed
   - Product Families
   - Standard Operation Flow
   - Operation Dictionary
   - Work Center Dictionary
   - Machine / Equipment Dictionary
   - Machine-To-Operation Map
   - Operation Step Summaries
   - Inspection And Test Points / Quality Gates
   - Likely Evidence Sources By Operation
   - Shop-Specific Terminology
   - Open Mapping Questions
   - Revision Notes
3. Generate `Shop Flow SME`.
4. Generate `Inspection SME`.
5. Detect named machines, stations, cells, benches, equipment assets, and major capabilities.
6. Create one Machine / Capability SME candidate for each detected item.
7. Map each candidate to operation numbers, operation names, work centers, route status, and source notes.
8. Apply `references/machine-capability-sme-rules.md`.
9. Apply `references/shop-flow-sme-rules.md`.
10. Apply `references/inspection-sme-rules.md`.
11. Apply `references/sme-status-classification-rules.md`.
12. Apply `references/router-ready-shell-rules.md`.
13. Apply `references/router-trigger-rules.md`.
14. Apply `references/sme-contribution-format.md`.
15. Apply `references/machine-to-sme-mapping-rules.md` for compatibility and edge-case guidance.
16. Use `references/sme-taxonomy.md` only as non-exhaustive naming examples for machine/capability shells.
17. Classify each SME as Required, Conditional, Optional / Capability Available, User-requested, Needs Review, or Not Detected.
18. Assign SME Source Type as Shop flow, Inspection coordinator, Machine / Capability, or User-requested.
19. Assign confidence as High, Medium, Low, or Unknown.
20. Assign source depth as Level 1 through Level 5.
21. Add exact/named triggers and semantic/plain-language triggers to every shell.
22. Add Router Contribution Format to every shell.
23. Create targeted open questions for low-confidence, unknown, ambiguous, or conflicting assignments.
24. Generate `sme-coverage.md`.
25. Generate router-ready `sme-registry.md`.
26. Generate standardized SME profile shells under `smes/`.
27. Validate output against the expectations in `tests/validation-report.md`.

Preserve operation numbers, operation names, work centers, machine names, equipment names, station names, and source wording exactly as written in the source.

## 8. Source-Depth Rules

Use `references/source-depth-rules.md`.

Default rules:

- Auto-generated SMEs from `shop-reference.md` default to Level 3.
- `Shop Flow SME` defaults to Level 3 from `shop-reference.md`.
- `Inspection SME` defaults to Level 3 from `shop-reference.md`.
- Machine / Capability SMEs default to Level 3 from `shop-reference.md`.
- User-requested SMEs with no supporting documents default to Level 1.
- Do not claim Level 2 unless public references are actually included or created.
- Do not claim Level 4 unless manuals, work instructions, process specs, acceptance criteria, datasheets, maintenance documents, or shop procedures are present.
- Do not claim Level 5 unless actual shop evidence is present.
- Do not infer evidence-backed status from the existence of a possible evidence source.

## 9. Confidence Rules

Use `references/confidence-rules.md`.

Default rules:

- High: named machine/capability is directly tied to a standard operation, or the source explicitly confirms the relationship.
- Medium: named machine/capability is tied to alternate, route-dependent, special, conditional, or partially resolved use.
- Low: machine/capability is listed but weakly linked, inactive, backup-only, or only generally described.
- Unknown: the source is too ambiguous to assign confidently.

When in doubt, choose the lower confidence and create an open question.

## 10. User-Requested SME Handling

Use `references/user-requested-sme-rules.md`.

Allow user-requested SMEs even when not detected from `shop-reference.md`. Mark them as User-requested. Default source depth to Level 1 unless supporting documents are provided. If the requested SME can be linked to existing operations or machines, mark that link as Possible or Conditional, not confirmed.

Do not claim the SME is part of standard flow unless `shop-reference.md` supports it.

## 11. Scope Guardrails

The SME Generator must not:

- perform RCCA
- determine root cause
- recommend corrective action
- analyze defects
- analyze SPC
- analyze machine performance
- interpret maintenance events
- parse production data
- claim process capability beyond source evidence
- answer management insight questions
- answer training questions
- answer technical SME questions
- create final SME knowledge packs
- scrape the web
- create vector databases
- create broad data/control/process SMEs from weak evidence alone

If a prompt asks for those activities, respond with the relevant SME or SMEs that would be needed and state that the answer belongs to a later SME pack or another skill.

## 12. Standard Output Format

Use `references/output-template.md` exactly for:

- `sme-coverage.md`
- `sme-registry.md`
- SME profile shell files under `smes/`

Each profile shell should use the standardized headings from `references/sme-profile-template.md`.

## 13. Validation Expectations

Before considering output ready, compare it against:

- `tests/cca-shop-reference-basic.md`
- `tests/machining-shop-reference.md`
- `tests/cable-harness-shop-reference.md`
- `tests/composite-shop-reference.md`
- `tests/generic-ambiguous-shop-reference.md`
- `tests/cca-shop-reference-with-optional-processes.md`
- `tests/ambiguous-shop-reference.md`
- `tests/add-esd-sme.md`
- `tests/add-hand-solder-sme.md`
- `tests/validation-report.md`

Validation must confirm that the skill:

- reads `shop-reference.md` correctly
- always generates `Shop Flow SME`
- always generates `Inspection SME`
- generates Machine / Capability SMEs from named machines, equipment, stations, cells, benches, and major capabilities
- does not rely on a hardcoded CCA/electronics taxonomy
- does not generate operation/task SMEs by default
- does not generate Kitting, MRB, Rework, Material Traceability, Maintenance / Equipment, or Testing SMEs by default unless represented as named capability/station/equipment or user-requested
- assigns status, confidence, and source depth correctly
- preserves operation numbers, names, work centers, machine names, and station names exactly
- creates targeted open questions
- generates `sme-coverage.md`, `sme-registry.md`, and SME profile shells
- includes router-ready shell sections in every profile
- includes exact/named and semantic/plain-language routing triggers as hints, not hard gates
- includes Router Contribution Format in every profile
- avoids RCCA, root cause, corrective action, process advice, and overclaiming shop capability
