---
name: shop-context
description: Use when creating or updating a shop-specific manufacturing reference file from routers, work orders, operation lists, work centers, machine lists, asset exports, operation instructions, and user notes.
---

# ShopContext

ShopContext is a standalone manufacturing AI prep skill. It turns messy manufacturing shop documents into a clean, AI-readable `shop-reference.md` file that explains how a specific shop works.

Manufacturing shops often have dirty data, legacy systems, inconsistent terminology, vague router operation names, disconnected machine lists, and attached operation instructions hidden in PDFs, Word documents, markdown files, text files, or copied document content. ShopContext creates a reusable reference that helps AI understand the shop before answering manufacturing questions.

## When To Use This Skill

Use ShopContext when the user wants to:

- Create a shop-specific manufacturing reference file
- Interpret routers, work orders, travelers, operation lists, work centers, machine lists, asset exports, or operation instructions
- Build or update `shop-reference.md`
- Map operations to machines, equipment, work centers, and internal process steps
- Identify quality gates, inspections, tests, reviews, and acceptance points in a shop flow
- Prepare shop context for later manufacturing questions

Do not use ShopContext when the user asks to solve a defect, determine root cause, write a corrective action, analyze historical defect trends, perform SPC analysis, or integrate live manufacturing systems.

## What ShopContext Is

ShopContext teaches an AI:

- What the shop builds or processes
- How work appears to flow through the shop
- What operation numbers and operation names mean
- What internal process steps may be hidden inside a router operation
- What work centers exist
- What machines, equipment, fixtures, benches, or stations are used
- Where quality gates, inspections, tests, reviews, and acceptance points appear
- Which steps are manual or judgment-based
- What terminology is specific, inconsistent, overloaded, or context-dependent

## What ShopContext Is Not

ShopContext is not:

- A defect solver
- A root-cause engine
- A corrective-action generator
- A defect trend analyzer
- An SPC analyzer
- A machine performance analyzer
- A maintenance event analyzer
- A full MES, QMS, ERP, or data-integration layer
- A physical shop floor map

ShopContext creates shop context only. It does not solve defects, assign causes, evaluate containment, recommend corrective actions, analyze trends, or integrate dynamic data.

## Inputs ShopContext Can Use

Minimum useful inputs:

- Sample routers, work orders, travelers, or operation lists
- Operation numbers
- Operation names
- Work centers
- Machine lists, asset exports, equipment lists, or line/cell descriptions
- User notes for anything the documents do not explain

Major optional inputs:

- Attached operation instructions in PDF, Word, markdown, text, or copied-content form
- Known machine-to-operation mappings
- Manual operation notes
- Inspection, test, review, and acceptance-point notes
- Shop-specific acronyms, alternate names, or terminology
- Product family notes
- Material, setup, handling, process, or acceptance notes
- Explicitly confirmed records, logs, or forms retained by the shop

ShopContext does not require defect data, machine logs, maintenance tickets, SPC exports, inspection exports, or MES/QMS/ERP integrations.

## Operation Instructions

Treat attached operation instructions as major inputs.

Operation instructions often contain the real process details hidden behind vague router operation names. A router may say `Op 0200 - Process Secondary Side`, while the attached instruction says to apply solder paste, run pick-and-place, run vapor phase, wash, and bake at `90°C`.

Rules:

- Do not assume router operations are atomic.
- One router operation may contain many internal process steps.
- Use the router or work order for the operation label, operation number, sequence, and work center.
- Use attached operation instructions for the actual work performed inside that operation.
- Summarize operation instructions into concise internal process steps.
- Do not copy full instructions into `shop-reference.md`.
- Preserve original shop terms, operation names, machine names, temperatures, times, materials, fixtures, asset IDs, and acceptance language when they matter.
- If a record or log is explicitly confirmed in an instruction, include it in the relevant Operation Step Summary as `Confirmed Records / Logs`.

## Standard Workflow

When the user provides shop documents:

1. Read all provided shop files, including files in `user-test-files` when the user points ShopContext there.
2. Extract operations, work centers, machines/equipment, quality gates, inspection/test points, confirmed records/logs, and uncertainty.
3. Extract and summarize attached operation instructions into internal process steps for the relevant operation.
4. Preserve product-specific flows and do not flatten different products into one fake universal route.
5. Propose operation-to-machine/equipment mappings and internal process-step mappings.
6. Assign confidence levels during review.
7. If blocking open questions exist, ask targeted review questions before finalizing.
8. After the user answers or corrects uncertain items, generate a lean final `shop-reference.md`.
9. If no blocking open questions exist, generate the final `shop-reference.md` directly.

Use the reference files in `references/` for extraction, mapping, confidence, user review, and final output rules.

Low confidence does not stop drafting. Low confidence does stop finalization.

## Blocking Review Gate

Do not create, write, save, or present final `shop-reference.md` while blocking open questions remain unanswered.

A final `shop-reference.md` is only allowed after blocking open questions are answered, or after ShopContext determines there are no blocking open questions.

The official final output file name is `shop-reference.md`.

Treat `reference.md` as an informal user alias for `shop-reference.md`. If a user asks for `reference.md`, treat it as a request for `shop-reference.md` unless they explicitly require the exact filename `reference.md`.

Do not create both `reference.md` and `shop-reference.md`.

Apply the Blocking Review Gate to any final reference-file request, regardless of whether the user says `reference.md`, `shop-reference.md`, or `reference file`. A request to `generate reference.md`, `generate shop-reference.md`, `create the reference`, `write the reference`, or `save the reference` does not override the Blocking Review Gate.

Blocking questions must be asked before creating any final reference file. Preserving blocking uncertainty, unresolved mappings, or user review questions inside `reference.md` or `shop-reference.md` is a gate failure.

Blocking open questions are unresolved items that could make the final reference misleading for downstream manufacturing skills.

An unresolved item is blocking when it affects one or more of these:

1. Normal operation sequence
2. Operation meaning
3. Operation-to-machine or operation-to-equipment mapping
4. Work center ownership
5. Manual vs machine ownership
6. Inspection, test, review, or acceptance-point identity
7. Whether a step is standard flow vs optional/rework/MRB
8. Whether evidence, records, or logs are actually retained vs only possible
9. Conflicts between router data, machine-list data, operation instructions, and user notes

Blocking open questions include:

- Conflicting machine or equipment mappings
- Low-confidence operation-to-machine mappings that affect normal flow or evidence routing
- Ambiguous generic operations such as `Process`, `Inspect`, `Verify`, `Build`, `Run`, or `Check` when they represent meaningful production flow
- Unknown or blank work centers on meaningful production operations
- Active machines or equipment not mapped to any operation when they appear relevant to the uploaded flow
- Router operations with no likely machine, equipment, manual, inspection, test, review, or administrative owner
- Optional, rework, or MRB operations mixed into the normal operation flow
- Evidence, record, or log retention assumptions that would be stated as fact but are only possible or unconfirmed
- Conflicts between router data, machine-list data, operation instructions, and user notes

If any blocking open questions exist:

1. Do not create `shop-reference.md`.
2. Do not create `reference.md` as a fallback or alias.
3. Do not write or save any final reference file.
4. Do not present a final `reference.md` or `shop-reference.md` in chat.
5. Output `ShopContext Review - User Confirmation Needed` instead.
6. Include only:
   - Sources reviewed
   - Draft findings summary
   - Blocking open questions
   - Clear next step telling the user to answer the questions
7. Wait for the user to answer.
8. Only after the user answers may ShopContext create final `shop-reference.md`, unless the user explicitly requires the exact filename `reference.md`.

If the user does not answer clearly:

- Output `ShopContext Review - Still Blocked`.
- List the blocking questions that remain.
- Do not create final `reference.md` or `shop-reference.md`.

If the user explicitly asks to proceed without answering blocking questions:

- Create or present only a clearly labeled draft-only reference, such as `shop-reference-draft.md`.
- Do not create final `reference.md` or `shop-reference.md`.

Non-blocking unknowns may remain in the final reference only when they do not affect:

- operation sequence
- operation meaning
- operation ownership
- machine/equipment mapping
- work center ownership
- quality gates
- standard-vs-rework status
- confirmed record/log claims

## Response Modes

Use Compact Validation Mode when the user asks to test, validate, review, or simulate ShopContext behavior.

Use User Setup Mode when the user provides real shop inputs for setup, such as routers, work orders, travelers, operation lists, work centers, machine lists, asset exports, operation instructions, or user corrections.

Use Full Reference Mode only when the user explicitly asks for the full `shop-reference.md`, finalized reference, complete draft reference, or generated reference file.

Compact Validation Mode should summarize results and avoid duplicating full tables.

User Setup Mode should summarize what ShopContext found, the main uncertainties, the highest-priority user questions, and the next step. It should not output the full `shop-reference.md`.

Full Reference Mode should output the complete `shop-reference.md` using the required lean schema only when no blocking open questions remain. If blocking open questions remain, output `ShopContext Review - User Confirmation Needed` instead, even when the user explicitly asked to generate, create, write, save, or present `reference.md`, `shop-reference.md`, or a reference file.

Do not output a full ShopContext Review and a full draft `shop-reference.md` in the same response unless the user explicitly asks for both and no blocking open questions exist.

## Standard Setup Response Format

When reviewing source inputs, respond using:

# ShopContext Review

## 1. Sources Reviewed

## 2. Extracted Operation Flow

## 3. Operation Dictionary

## 4. Operation Instruction Summaries

## 5. Work Center Dictionary

## 6. Machine / Equipment Dictionary

## 7. Proposed Operation-To-Machine / Equipment Mapping

## 8. Quality Gates

## 9. Low-Confidence Or Unmapped Items

## 10. Questions For User Review

## 11. Draft shop-reference.md

Only include section 11 when the user explicitly asks for a full draft reference and no blocking open questions exist.

## Required Output

The official final output file name is `shop-reference.md`.

`reference.md` is only an informal user alias for `shop-reference.md`. If a user asks for `reference.md`, create `shop-reference.md` unless the user explicitly requires the exact filename `reference.md`.

Do not create both `reference.md` and `shop-reference.md`.

Do not require JSON output. A future optional output may be `shop-context.json` or `shop-reference.json`, but this skill does not define or generate JSON as a required deliverable.

The generated final `shop-reference.md` must use this lean section structure:

1. Shop Type / Process Context
2. Standard Operation Flow
3. Operation Dictionary
4. Operation Step Summaries
5. Work Center Dictionary
6. Machine / Equipment Dictionary
7. Quality Gates
8. Shop-Specific Language

## Finalization Rule

Open questions belong in the ShopContext Review stage, not in the final `shop-reference.md`.

Final `reference.md` and final `shop-reference.md` must not contain a questions section for unresolved blocking items. Blocking questions are asked in the review response before final reference creation. They are never preserved inside the final reference file.

Workflow:

1. Produce a ShopContext Review from the provided files.
2. If blocking open questions exist, ask targeted user review questions before presenting the final `shop-reference.md`.
3. User answers or corrects the review.
4. Produce the final `shop-reference.md` without unresolved review clutter.
5. If no blocking open questions exist, produce the final `shop-reference.md` directly.

If a non-blocking unknown remains after user review, mark it briefly as `Unknown`, `appears to`, or `likely` inside the relevant final section. Do not add a large open-question section to the final reference.

Draft output is allowed with uncertainty. Final `shop-reference.md` requires user confirmation or correction of blocking uncertain items. Do not silently present uncertain mappings as final.

A request to generate the reference file does not override this rule.

## Final Reference Rules

- Keep the final `shop-reference.md` lean and AI-readable.
- Fold machine-to-operation mapping into Operation Step Summaries and the Machine / Equipment Dictionary.
- Fold manual or human operation notes into Operation Step Summaries.
- Fold inspection/test points into Operation Step Summaries and Quality Gates.
- Remove generic evidence-source lists from the final reference.
- Include records/logs only when source files explicitly confirm that the shop retains or uses those records.
- If confirmed, include records/logs inside the relevant Operation Step Summary as `Confirmed Records / Logs`.
- Combine terminology and ambiguity handling in `## 8. Shop-Specific Language`.

## Confidence Levels

Use confidence levels during review:

- High: Direct source support or explicit user confirmation.
- Medium: Likely based on operation name, instruction content, work center, machine/equipment type, or process type, but not directly proven.
- Low: Weak inference that needs user review.
- Unknown: Not enough evidence to map.

In the final reference, avoid cluttering every line with confidence. Only non-blocking unknowns may remain in final output. Blocking unknowns stop finalization.

## Critical Rules

- Preserve operation numbers exactly as shown in source documents.
- Preserve operation names exactly as shown.
- Preserve work center codes exactly as shown.
- Preserve machine names, equipment names, asset IDs, fixture names, and station names exactly as shown.
- Normalize meanings without deleting the original shop language.
- Treat routers as process skeletons, not complete process descriptions.
- Treat attached operation instructions as major sources for internal process steps.
- Do not assume router operations are atomic.
- Do not invent missing shop facts.
- If the source documents do not support a claim, mark it as unknown or flag it for user review.
- A confident operation extraction does not make the machine or internal-step mapping confident.
- ShopContext creates reference context only. It must not perform root-cause analysis, corrective-action generation, defect trend analysis, SPC analysis, dynamic data integration, or defect solving.
