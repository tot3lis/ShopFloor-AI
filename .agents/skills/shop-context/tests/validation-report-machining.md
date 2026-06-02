# Validation Report - Machining Edge-Case Package

Manual validation expectations for the ShopContext machining / precision metal fabrication edge-case package. These are synthetic markdown checks, not executable tests.

## Files In Package

- `sample-router-machining-shared-wo.md`
- `sample-prt-machining-multi-op-instruction.md`
- `sample-machine-list-machining-unmapped.md`
- `sample-shop-notes-machining.md`
- `expected-shop-reference-behavior-machining.md`

## Scenario Being Tested

This package validates a different shop type and document structure than the CCA hidden-step package.

The test shop is a machining / precision metal fabrication shop making `AL-BRACKET-782 Rev C` from `6061-T6 aluminum`.

The edge cases are:

- One PRT/traveler instruction document contains multiple operation instruction sections.
- One WO/traveler number, `WO-MACH-44591`, is reused across multiple operations.
- The machine list does not explicitly map machines to operation numbers.
- CNC work center `2200` has multiple possible mills.
- ShopContext must infer likely machine/equipment context from operation headers, instruction content, work centers, machine types, and shop notes without inventing exact machine assignments.

## Pass / Fail Criteria

| # | Criterion | Pass Condition |
|---|---|---|
| 1 | PRT multi-operation splitting works | `sample-prt-machining-multi-op-instruction.md` is split by operation headers into operation-specific summaries for Ops `0100` through `0700`. |
| 2 | Reused WO/traveler handled correctly | Repeated `WO-MACH-44591` does not cause operations to be collapsed or merged. |
| 3 | Unmapped machine list still useful | Machine list supports likely equipment context even though it contains no operation numbers. |
| 4 | Ambiguity remains uncertain | Exact CNC mill assignment is not asserted as fact when `M-12` does not clearly map to `Haas VF-2SS CNC Mill` or `Haas VF-4 CNC Mill`. |
| 5 | Operation Step Summaries are rich but concise | Summaries include internal steps, likely tools/machines, manual notes, and quality gates when supported by the PRT, router, machine list, or shop notes. |
| 6 | Lean final structure preserved | Final `shop-reference.md` uses only the updated 8-section structure. |
| 7 | No generic evidence-source section | Final output does not include generic Evidence Sources, Likely Records To Check, or similar standalone sections. |
| 8 | No final open-question section | Open questions remain in review output only, not in final `shop-reference.md`. |
| 9 | Standalone scope maintained | Output does not drift into RCCA, root cause analysis, corrective action, trend analysis, SPC analysis, dynamic data integration, or larger-system routing. |

## Expected Extraction Checks

- Operation numbers are preserved exactly: `0100`, `0200`, `0300`, `0400`, `0500`, `0600`, `0700`.
- Operation names are preserved exactly: `Material Issue`, `Machine 1st Side`, `2nd Op Machine`, `Deburr`, `Chem Film`, `Final Insp`, `Pack / Closeout`.
- Work centers are preserved exactly: `1000`, `2200`, `2300`, `2400`, `3100`, `9000`.
- Part, revision, material, and WO/traveler context are preserved: `AL-BRACKET-782 Rev C`, `6061-T6 aluminum`, `WO-MACH-44591`.
- Alternate naming is normalized without deleting original terms:
  - `Machine First Side` / `Machine 1st Side`
  - `2nd Op Machine` / second-side machining
  - `Deburr` / `Edge Break`
  - `Chem Film` / `Alodine`
  - `Final Insp` / `Final Inspection`

## Expected Operation Step Summary Checks

- Op `0100 Material Issue` includes pulling `6061-T6 aluminum`, material cert verification, blank-size verification, and traveler stamping.
- Op `0200 Machine 1st Side` includes CNC Mill `M-12`, fixture `FX-BRKT-782-A`, program `BRKT782_SIDE1_REV-C`, rough milling, drilling mounting holes, chamfering top edges, and in-process inspection of datum A and hole pattern.
- Op `0300 2nd Op Machine` includes fixture `FX-BRKT-782-B`, program `BRKT782_SIDE2_REV-C`, backside pocket finishing, drilling/countersinking remaining holes, thickness verification, and flatness inspection.
- Op `0400 Deburr` includes hand deburr, limited Scotch-Brite use, datum-edge protection, and chip removal.
- Op `0500 Chem Film` includes chem film area, masking threaded inserts if present, Class 3 chem film, and coverage check.
- Op `0600 Final Insp` includes drawing dimensions, hole pattern, finish, chem film coverage, optional CMM use when dimensional report is required, and traveler acceptance.
- Op `0700 Pack / Closeout` includes signoff completion, protective packaging, material cert copy when required, and WO closeout.

## Expected Machine / Equipment Handling

- `CNC-012 Haas VF-2SS CNC Mill` and `CNC-014 Haas VF-4 CNC Mill` are listed as possible CNC resources for work center `2200`, but exact assignment to `M-12` remains uncertain.
- `BENCH-DB-02 Manual Deburr Bench` and `DBR-017 Scotch-Brite Wheel` are likely context for Op `0400`.
- `CHEM-AL-03 Chem Film Tank Line` is likely context for Op `0500`.
- `CMM-006 CMM Zeiss Contura` and `INS-HT-02 Height Gauge Station` are possible/likely inspection equipment for Op `0600`, with CMM conditional on dimensional-report requirements.
- `LSR-001 Laser Marking Station` remains unmapped.
- `Old Bridgeport Mill` remains incomplete/ambiguous with `Unknown` work center.

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
- Machine performance analysis
- Maintenance event analysis
- Dynamic data integration
- ProblemPath or larger-system routing

## Ready For Simulated Validation

This package is ready for a simulated ShopContext run when the model can:

- Generate a ShopContext Review with review-stage questions.
- Generate a lean draft final `shop-reference.md`.
- Compare the draft against `expected-shop-reference-behavior-machining.md`.
- Preserve uncertainty where machine assignment is not proven.
