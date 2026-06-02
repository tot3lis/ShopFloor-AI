# Validation Report

Manual validation expectations for the ShopContext scaffold. These are synthetic markdown checks, not executable tests.

## sample-router-basic.md

Expected behavior:

- Extract operations from the CSV-style router table.
- Preserve operation numbers exactly.
- Preserve operation names exactly.
- Preserve numeric work centers exactly.
- Avoid renaming numeric work centers unless the meaning is clearly labeled as inferred.
- Use `user_note` as context, not proof of actual execution.
- Infer likely plain-English meaning from operation names and notes where reasonable.
- Identify inspection and test points from operation names and notes.
- Identify likely manual operations when supported by names and notes.
- Avoid over-interpreting generic operation names such as `Inspect`.
- Treat router as planned flow, not evidence that a specific unit completed the route.

## sample-router-multiple-products.md

Expected behavior:

- Extract both product flows from the CSV-style router table.
- Preserve product-specific flows.
- Avoid flattening CCA-A and CCA-B into one fake universal route.
- Mark CCA-A Op 020 `Screen Print` and CCA-B Op 025 `Stencil Print` as possible equivalents, not proven equivalents.
- Mark CCA-A Op 030 `Place Components` and CCA-B Op 035 `Pick Place` as possible equivalents, not proven equivalents.
- Keep MRB Disposition and Rework Repair separate from standard flow unless the source says they are standard.
- Preserve numeric work centers exactly.
- Label inferred work center meanings as inferred.
- Treat user notes as context only, not proof of actual execution.

## sample-machine-list.md

Expected behavior:

- Extract machine records from the CSV-style machine export.
- Preserve machine names exactly.
- Preserve machine types exactly.
- Preserve numeric work centers exactly.
- Mark empty work centers as `Unknown`.
- Avoid assuming one work center equals one machine.
- Allow multiple machines in the same work center.
- Avoid forcing one-to-one operation-to-machine mapping.
- Flag Bench A and Bench B as ambiguous candidates for manual/final inspection.
- Flag Legacy Reflow Oven as conflicting or unmatched.
- Keep Conformal Coat Booth visible as unmapped if no router operation matches it.
- Avoid creating generic evidence-source lists.
- Avoid claiming logs, images, records, recipes, or result files are retained unless explicitly stated.

## ambiguous-machine-mapping.md

Expected behavior:

- Extract operations and machines from messy CSV-style sections.
- Preserve numeric-only work centers exactly.
- Mark missing operation or machine work centers as `Unknown`.
- Preserve generic operation names such as `Assembly`, `Process`, `Inspect`, and `Test`.
- Avoid treating generic operation names as enough evidence for High confidence.
- Avoid treating numeric work center match alone as proof of mapping.
- Assign confidence per mapping row.
- Use Low or Unknown confidence where appropriate.
- Use `No dedicated machine identified` when a manual operation lacks a supported machine.
- List multiple candidate machines instead of choosing one without support.
- Keep machines with no matching operation visible.
- Preserve optional, rework, alternate, and conditional route roles separately from standard flow.
- Create targeted open questions tied to exact operations, work centers, or machines.

## Realistic CCA Hidden-Steps Package

Files:

- `sample-router-with-hidden-steps.md`
- `sample-attached-work-instruction-op0200.md`
- `sample-machine-list-realistic.md`
- `sample-shop-notes.md`
- `expected-shop-reference-behavior.md`

Purpose:

- Validate the updated standalone ShopContext behavior using a realistic electronics/CCA package.
- Validate that routers/work orders provide operation labels and sequence.
- Validate that attached operation instructions provide internal process steps.
- Validate that router operations are not assumed to be atomic.
- Validate that final `shop-reference.md` output is lean and review clutter is excluded.

Expected behavior:

- Extract the work-order/router operations from `sample-router-with-hidden-steps.md`.
- Preserve operation numbers exactly: `0100`, `0200`, `0300`, `0400`, `0500`, `0600`.
- Preserve operation names exactly, including `Process Secondary Side`, `Primary Side Process`, and `E-Test`.
- Preserve numeric work centers exactly: `1000`, `2110`, `2210`, `3100`, `4100`.
- Treat `Op 0200 - Process Secondary Side` as a router operation container, not as one atomic process step.
- Recognize `sample-attached-work-instruction-op0200.md` as the detailed instruction for `0200 Process Secondary Side`.
- Summarize the Op `0200` instruction into main internal steps: solder paste application, pick-and-place, vapor phase reflow, wash, bake at `90°C`, and post-process inspection.
- Preserve important equipment names and asset IDs from the instruction and machine list.
- Map `DEK Horizon`, `MY200`, `VAC 545`, `Aqueous Washer AW-3`, and `Blue M Bake Oven` inside the Op `0200` Operation Step Summary when supported.
- Recognize `traveler` signoffs and oven load/unload time as confirmed records/logs because the instruction explicitly requires them.
- Map `Koh Young Zenith` to AOI/inspection context and `Electrical Test Station ETS-7` to `0500 E-Test` when supported.
- Keep `Conformal Coat Booth` and `Spare Hot Plate` visible as unmapped or ambiguous equipment.
- Use `sample-shop-notes.md` to normalize language such as `VP`, `Sec side`, `Pri side`, `PNP`, `E-Test`, `Electrical Test`, and `Functional Test`.
- Keep alternate names and overloaded language in `Shop-Specific Language`.

Pass/fail criteria:

| Criterion | Pass Condition |
|---|---|
| a. Preserve raw identifiers | Operation numbers, operation names, work center codes, machine names, and asset IDs are preserved exactly. |
| b. Recognize attached instruction | The Op `0200` work instruction is treated as the source of internal steps. |
| c. Avoid atomic-router assumption | Op `0200` is not treated as a single atomic operation. |
| d. Summarize instruction | The work instruction is summarized into main process steps, not copied in full. |
| e. Map machines/tools in summaries | Likely equipment appears inside Operation Step Summaries, especially for Op `0200`. |
| f. Fold quality context | Inspection/test context appears in Operation Step Summaries and Quality Gates. |
| g. Avoid generic evidence lists | No generic evidence-source or likely-records standalone section is generated. |
| h. Keep open questions out of final | Open questions appear in review only, not final `shop-reference.md`. |
| i. Combine terminology and ambiguity | Acronyms, alternate names, and overloaded terms appear in Shop-Specific Language. |
| j. Stay in scope | No root cause, corrective action, defect trend, SPC, dynamic integration, or larger-system routing behavior appears. |

## CSV-Style Input Handling

- Can ShopContext extract operations from CSV-style tables?
- Can it extract machine records from CSV-style tables?
- Does it preserve raw column values exactly?

## Numeric Work Centers

- Are numeric work centers preserved exactly?
- Does the output avoid renaming numeric work centers as SMT, Test, Inspection, or other plain-English names unless labeled as inferred?
- Does it use operation names, machine types, and user notes to infer possible meaning carefully?

## Non-One-To-One Work Centers

- Does the output avoid assuming one work center equals one machine?
- Can multiple machines exist in one work center?
- Can one machine support multiple operations when supported?
- Can one operation have multiple candidate machines when unresolved?
- Does the output preserve uncertainty when a shared machine supports multiple operations but the exact relationship is unclear?

## User Notes

- Are user notes used as context?
- Does the output avoid treating user notes as proof of actual execution?
- Does it separate source-supported facts from inferred context?

## Messy Export Limitations

- Missing work centers become `Unknown`.
- Generic operation names are preserved and not over-interpreted.
- Conflicting machine/work center data is preserved and flagged.
- Unmapped machines remain visible.
- Optional/rework/alternate operations remain separate from standard flow.

## Operation Instruction Handling

- Are attached operation instructions treated as major inputs?
- Can ShopContext handle operation instructions supplied as PDF, Word, markdown, text, or copied content?
- Does it summarize instructions into internal process steps instead of copying full instructions?
- Does it preserve important source details such as times, temperatures, materials, machine names, fixture names, asset IDs, and acceptance language?
- Does it avoid assuming router operations are atomic?
- Can one router operation contain multiple internal process steps and multiple machines/equipment items?
- Does it flag vague router operations when no matching instruction is provided?

## Confirmed Records / Logs Discipline

- Generic evidence-source lists are not included in the final reference.
- Records/logs/forms/results are included only when retention or use is explicitly confirmed by source files or user confirmation.
- Confirmed records/logs are placed inside the relevant Operation Step Summary.

## Draft Output With Unresolved Questions

- Does ShopContext still produce a draft `shop-reference.md` when open questions remain?
- Are unresolved items clearly labeled?
- Are open questions kept in the ShopContext Review stage rather than the final reference?
- If uncertainty remains after review, is it marked briefly inside the relevant final section?

## Uncertainty Labels

Check for use of:

- `Unknown`
- `Possible`
- `Inferred`
- `Low confidence`
- `Needs user review`

## Alternate / Optional / Rework Route Separation

- Are rework, optional, alternate, disposition, and closeout operations kept separate from standard flow?

## Router Planned-Flow Limitation

- Does the output avoid claiming that a specific unit actually followed the route?
- Does it treat routers as intended or planned process skeletons?

## Manual Operation Handling

- Does the output avoid forcing fake machine mappings for manual, administrative, inspection-only, or handling-based steps?
- Does it use `No dedicated machine identified` when appropriate?

## Confidence Behavior

- Is confidence assigned per mapping row?
- Are operation extraction confidence and machine mapping confidence kept separate?
- Are low or unknown mappings turned into targeted open questions?
- Is an optional `Source`, `Product`, or `Route` column used only when it reduces ambiguity?

## Output Length Control

- Is compact validation output the default for test, validation, review, or simulation prompts?
- Does compact validation avoid duplicating full operation, work center, mapping, instruction-summary, and quality-gate tables?
- Is full `shop-reference.md` output still available when explicitly requested?
- Does the output avoid providing a full ShopContext Review and a full draft `shop-reference.md` in the same response unless explicitly requested?
- Does the final reference use the lean 8-section structure?
- Does the final reference avoid standalone sections for Source Documents Reviewed, Product Families, Machine-To-Operation Map, Manual / Human Operations, Likely Evidence Sources, Open Mapping Questions, and Revision Notes?

## User Setup Mode

- Does User Setup Mode exist?
- Is User Setup Mode the default when a real user provides shop setup inputs such as routers, work orders, operation lists, work centers, machine lists, asset exports, or user notes?
- Does User Setup Mode include attached operation instructions as real shop setup inputs?
- Does User Setup Mode avoid generating the full `shop-reference.md` by default?
- Does User Setup Mode provide a short `ShopContext Setup Review` with what was found, what is uncertain, targeted questions, and the next step?
- Does User Setup Mode ask 5-10 high-priority questions instead of every possible open question?
- Are optional confirmed-record/log questions clearly marked optional?
- Does User Setup Mode tell the user that the full `shop-reference.md` will only be generated when requested?
- Does Full Reference Mode still work when explicitly requested?
- Does Compact Validation Mode still work for validation/testing prompts?

## Core Logic Stability

- Does the core ShopContext logic preserve source language while summarizing messy shop documents?
- Are numeric work centers still preserved exactly?
- Does uncertainty remain visible using labels such as `Unknown`, `Possible`, `Inferred`, `Low confidence`, and `Needs user review`?
- Does the skill still produce a draft reference when open questions remain?
- Are confidence labels used during review without cluttering every final-reference line?

## Lean Final Reference Structure

The final `shop-reference.md` should use:

1. Shop Type / Process Context
2. Standard Operation Flow
3. Operation Dictionary
4. Operation Step Summaries
5. Work Center Dictionary
6. Machine / Equipment Dictionary
7. Quality Gates
8. Shop-Specific Language

## Scope Control

Confirm the output does not perform:

- Root cause analysis
- Corrective action generation
- Defect trend analysis
- SPC analysis
- Machine performance analysis
- Maintenance event analysis
- Data integration
- Any larger-system routing or handoff behavior

## Pass Criteria

The scaffold passes validation when it can guide Codex to create a practical, manufacturing-specific `shop-reference.md` from rough manufacturing software exports and attached operation instructions while preserving raw source values, summarizing internal process steps, keeping review-stage uncertainty visible, and staying strictly within shop-context creation.

## Public Repo Cleanup

Validation note:

- Real-use CCA shop test data was removed from the public repo test set.
- Remaining tests are synthetic examples intended for public validation.
- User Setup Mode remains the default for real shop setup inputs.
- Full Reference Mode remains available when explicitly requested.
- Compact Validation Mode remains available for validation/testing prompts.
- Scope stays within standalone ShopContext manufacturing AI prep.
- Required patches: none.
- Optional improvements: add future public-safe setup examples using fully synthetic operation instructions, including vague router operations with detailed attached instructions.
