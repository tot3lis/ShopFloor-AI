# Expected Shop Reference Behavior

This file describes the expected ShopContext behavior for the realistic CCA/electronics test package:

- `sample-router-with-hidden-steps.md`
- `sample-attached-work-instruction-op0200.md`
- `sample-machine-list-realistic.md`
- `sample-shop-notes.md`

## Final Reference Structure

The final output should use the updated lean structure:

```md
# Shop Reference

## 1. Shop Type / Process Context

## 2. Standard Operation Flow

## 3. Operation Dictionary

## 4. Operation Step Summaries

## 5. Work Center Dictionary

## 6. Machine / Equipment Dictionary

## 7. Quality Gates

## 8. Shop-Specific Language
```

## Required Behavior

- Preserve operation numbers exactly: `0100`, `0200`, `0300`, `0400`, `0500`, `0600`.
- Preserve operation names exactly, including inconsistent terms such as `Process Secondary Side`, `Primary Side Process`, and `E-Test`.
- Preserve work center codes exactly: `1000`, `2110`, `2210`, `3100`, `4100`.
- Treat the router/work order as the source of operation labels and sequence.
- Treat `sample-attached-work-instruction-op0200.md` as the source of internal process details for `0200 Process Secondary Side`.
- Do not treat `0200 Process Secondary Side` as a single atomic operation.
- Decompose and summarize operation `0200` into the main internal steps:
  - solder paste application
  - pick-and-place
  - vapor phase reflow
  - wash
  - bake at `90°C`
  - post-process inspection
- Do not copy the full work instruction into the final reference.
- Fold likely machine/equipment mapping into `## 4. Operation Step Summaries` and `## 6. Machine / Equipment Dictionary`.
- Fold manual notes, setup notes, quality checks, and test/inspection context into Operation Step Summaries and Quality Gates.
- Include confirmed records/logs only where explicitly supported. For this package, the Op `0200` instruction explicitly confirms traveler signoffs and oven load/unload time.
- Put alternate names and overloaded terms in `## 8. Shop-Specific Language`.

## Sections That Should Not Appear In Final Output

The final `shop-reference.md` should not include standalone sections named:

- Evidence Sources
- Likely Evidence Sources By Operation
- Likely Records To Check
- Generic Records To Check
- Open Questions
- Open Mapping Questions
- Questions For User Review
- Machine-To-Operation Map
- Manual / Human Operations
- Revision Notes

Open questions should appear during the ShopContext Review stage only. If something remains unresolved in the final reference, it should be marked briefly as `Unknown`, `appears to`, or `likely` inside the relevant section.

## Scope Guardrails

The output must stay within ShopContext scope. It should not perform root-cause analysis, corrective-action generation, defect trend analysis, SPC analysis, machine performance analysis, maintenance analysis, dynamic data integration, or any larger-system routing.
