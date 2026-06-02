# Validation Report - Bad Input Quality

Manual validation expectations for the bad-input-quality CCA/electronics package. These are synthetic markdown checks, not executable tests.

## Files In Package

- `sample-router-bad-input-quality.md`
- `sample-prt-cca-ctrl-9001-smt.md`
- `sample-prt-cca-pwr-9010-unclear-headers.md`
- `sample-machine-list-bad-quality.md`
- `sample-shop-notes-bad-quality.md`
- `expected-shop-reference-behavior-bad-input-quality.md`

## Scenario Being Tested

This package validates graceful uncertainty handling when the uploaded shop documents are messy, incomplete, contradictory, and duplicative.

The edge cases are:

- Missing instruction for `CCA-CTRL-9002`.
- Poorly formatted instruction headers for `CCA-PWR-9010`.
- Router-vs-PRT contradiction for `CCA-CTRL-9001` wash requirement.
- Duplicate/conflicting machine names and asset IDs.
- Contradictory shop notes and source values.
- Missing work centers.
- Repeated inspection operations with unclear AOI/manual split.

## Pass / Fail Criteria

| # | Criterion | Pass Condition |
|---|---|---|
| 1 | Missing instruction handling works | `WI-CCA-9002-SMT.docx` is flagged as missing and internal steps are not fabricated. |
| 2 | Poor PRT headers handled with uncertainty | `CCA-PWR-9010` sections are probably matched to router operations but not asserted as clean exact matches. |
| 3 | Router-vs-PRT contradiction detected | `CCA-CTRL-9001` router note says no wash, while PRT requires wash/bake. |
| 4 | Shop notes resolve without erasing conflict | Shop notes support wash required for `CCA-CTRL-9001`, but final reference preserves the source conflict. |
| 5 | Duplicate machines/assets detected | Likely aliases and duplicate asset IDs are identified without silently collapsing the machine list. |
| 6 | Retired machine excluded from active context | `Old Washer Line` is marked retired/stale and not treated as active equipment. |
| 7 | Conflicting work centers preserved | VP work centers `2110` and `2120` remain visible. |
| 8 | Repeated inspections remain distinct/uncertain | `0400 Inspect` and `0450 Inspect` are not incorrectly merged. |
| 9 | Machine list supports context without fake certainty | Equipment context is likely/possible unless operation mapping is source-supported. |
| 10 | Lean final structure | Final output uses the updated 8-section structure. |
| 11 | No generic evidence-source section | Final output does not include generic Evidence Sources or Likely Records To Check sections. |
| 12 | No final open-question section | Open questions remain review-stage only. |
| 13 | Standalone scope maintained | Output does not drift into RCCA, root cause analysis, corrective action, trend analysis, SPC analysis, dynamic data integration, or larger-system routing. |

## Expected Extraction Checks

- Part numbers and revisions are preserved: `CCA-CTRL-9001 Rev A`, `CCA-CTRL-9002 Rev B`, `CCA-PWR-9010 Rev C`.
- Operation numbers are preserved exactly, including `0010`, `0020`, and `0250`.
- Blank work center for `CCA-PWR-9010 0250 Clean / Bake` is marked `Unknown`.
- Missing instruction `WI-CCA-9002-SMT.docx` remains visible in review-stage uncertainty.
- `Old Washer Line` is not used as active washer context.

## Expected Machine / Equipment Handling

- `DEK Horizon` / `DEK Horizon 03` are likely aliases.
- `MY200` / `MY-200 PNP` are likely aliases.
- `VAC 545` / `Vapor Phase Oven` are likely the same asset but retain conflicting work centers.
- `Aqueous Washer AW-3` keeps `Unknown` work center from the machine list.
- `AOI Review Station` remains generic/uncertain because asset ID is blank.

## Expected Final Reference Structure

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

- RCCA
- Root cause analysis
- Corrective action generation
- Defect trend analysis
- SPC analysis
- Dynamic data integration
- ProblemPath or larger-system routing

## Ready For Simulated Validation

This package is ready for a simulated ShopContext run when the model can:

- Generate a ShopContext Review with review-stage questions.
- Generate a lean draft final `shop-reference.md`.
- Compare the draft against `expected-shop-reference-behavior-bad-input-quality.md`.
- Preserve uncertainty without hallucinating clean mappings.
