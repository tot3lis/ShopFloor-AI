# Validation Report - Harness Five PNs

Manual validation expectations for the cable / harness manufacturing multi-part-number package. These are synthetic markdown checks, not executable tests.

## Files In Package

- `sample-router-harness-five-pns.md`
- `sample-prt-harn-1001.md`
- `sample-prt-harn-1002.md`
- `sample-prt-harn-1003.md`
- `sample-prt-harn-1004.md`
- `sample-prt-harn-1005.md`
- `sample-machine-list-harness-unmapped.md`
- `sample-shop-notes-harness.md`
- `expected-shop-reference-behavior-harness-five-pns.md`

## Scenario Being Tested

This package validates a cable / harness manufacturing shop with five part numbers that share a broad manufacturing pattern but differ in operation names and operation granularity.

The edge cases are:

- Multiple routers/work orders across different part numbers.
- Same-meaning operations named differently across part numbers.
- One part number splitting a process into two operations while another combines those steps into one operation.
- PRT documents for each part number reveal the actual internal work.
- Vague operation names such as `Process Leads` must be decomposed from PRT content.
- Machine list has no operation-number or part-number mappings.

## Pass / Fail Criteria

| # | Criterion | Pass Condition |
|---|---|---|
| 1 | Multi-PN pattern recognition works | The output recognizes one harness shop/process family across five PNs. |
| 2 | Same-meaning operations are grouped | Naming variants such as `Wire Prep`, `Cut / Strip`, `Prep Leads`, and `Lead Prep` are grouped as related wire-prep language. |
| 3 | PN-specific differences are preserved | Each part number keeps its own operation numbers, names, work centers, and granularity. |
| 4 | Combined operations are decomposed | `Terminate / Sleeve Leads`, `Crimp / Solder`, and `Process Leads` are decomposed using PRT content. |
| 5 | Split operations are recognized | `Cut Wires` + `Strip Leads` are recognized as equivalent to combined wire-prep operations in other PNs. |
| 6 | Vague names are not atomic | `Process Leads` is not treated as one opaque step. |
| 7 | Machine list supports context without fake certainty | Equipment is described as likely/possible unless exact PN/op assignment is source-supported. |
| 8 | Lean final structure | Final output uses the updated 8-section structure. |
| 9 | No generic evidence section | Final output does not include generic Evidence Sources or Likely Records To Check sections. |
| 10 | No final open questions | Open questions remain review-stage only. |
| 11 | Standalone scope maintained | Output does not drift into RCCA, root cause analysis, corrective action, trend analysis, SPC analysis, dynamic data integration, or larger-system routing. |

## Expected Extraction Checks

- Part numbers and revisions are preserved: `HARN-1001 Rev A`, `HARN-1002 Rev B`, `HARN-1003 Rev C`, `HARN-1004 Rev A`, `HARN-1005 Rev D`.
- Operation numbers are preserved exactly, including `0250` for `HARN-1003`.
- Work centers are preserved exactly: `1000`, `2100`, `2200`, `2300`, `2400`, `3100`, `4100`, `9000`.
- PRT operation sections are linked to corresponding router operations for each PN.
- The reference does not erase messy original terms.

## Expected Granularity Checks

- `HARN-1001` separates crimp and heat shrink.
- `HARN-1002` combines termination and sleeve/heat shrink.
- `HARN-1003` splits cut and strip.
- `HARN-1004` combines cut and strip as `Prep Leads`.
- `HARN-1005` uses vague `Process Leads`, which is decomposed into strip verification, crimp, solder splice, sleeve, heat shrink, and pull-test.

## Expected Machine / Equipment Handling

- Wire prep equipment is likely associated with work center `2100`, but exact PN/op assignment remains uncertain.
- Crimp equipment is likely associated with work center `2200`, but exact PN/op assignment remains uncertain.
- Solder and heat equipment are likely associated with work center `2300`.
- Harness layout board table is likely associated with work center `2400`.
- Continuity tester is likely associated with work center `3100`.
- Hipot tester is possible/conditional, not assumed for every harness.
- Label printer may support pack/closeout, but exact operation use is not asserted unless supported by PRT content.
- Ultrasonic welder remains unmapped.
- Obsolete hand crimper remains incomplete/ambiguous.

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

- Generate a ShopContext Review across all five part numbers.
- Generate a lean draft final `shop-reference.md`.
- Compare the draft against `expected-shop-reference-behavior-harness-five-pns.md`.
- Preserve operation granularity differences while identifying common shop process patterns.
