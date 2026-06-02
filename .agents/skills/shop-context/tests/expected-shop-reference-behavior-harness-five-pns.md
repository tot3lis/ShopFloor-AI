# Expected Shop Reference Behavior - Harness Five PNs

This file describes expected ShopContext behavior for the cable / harness manufacturing multi-part-number package:

- `sample-router-harness-five-pns.md`
- `sample-prt-harn-1001.md`
- `sample-prt-harn-1002.md`
- `sample-prt-harn-1003.md`
- `sample-prt-harn-1004.md`
- `sample-prt-harn-1005.md`
- `sample-machine-list-harness-unmapped.md`
- `sample-shop-notes-harness.md`

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

## Expected Pass Behavior

- Recognize the shop as cable / harness manufacturing.
- Handle five part numbers without creating five totally separate unrelated shop references.
- Preserve each part number, revision, operation number, operation name, and work center.
- Group same-meaning operations with different names.
- Preserve PN-specific operation differences.
- Recognize operation granularity differences:
  - `HARN-1001 Rev A` separates `Crimp Contacts` and `Apply Heat Shrink`.
  - `HARN-1002 Rev B` combines termination and sleeve/heat shrink as `Terminate / Sleeve Leads`.
  - `HARN-1003 Rev C` splits wire prep into `Cut Wires` and `Strip Leads`.
  - `HARN-1004 Rev A` combines cut and strip as `Prep Leads`.
  - `HARN-1005 Rev D` uses vague `Process Leads`.
- Decompose vague or combined operations using each PRT.
- Recognize that `Process Leads` includes strip verification, crimp contacts, solder splice, sleeve, heat shrink, and pull-test sample crimps.
- Recognize that `Cut Wires` + `Strip Leads` together overlap with `Wire Prep`, `Cut / Strip`, `Prep Leads`, and `Lead Prep`.
- Recognize that `Buzz Out`, `Continuity Test`, `E-Test`, `Electrical Test`, and `Test` are related electrical-test language.
- Do not flatten everything into one generic flow without preserving PN-specific differences.
- Do not create fake machine-to-operation mappings from the machine list.
- Use `likely`, `appears to`, or `possible` language when exact equipment assignment is not proven.
- Do not output a generic Evidence Sources or Likely Records To Check section.
- Do not include Open Questions in the final `shop-reference.md`.
- Combine acronyms, alternate names, overloaded terms, and granularity warnings into `Shop-Specific Language`.
- Do not perform RCCA, root cause analysis, corrective action, defect trend analysis, SPC analysis, dynamic data integration, or larger-system routing.

## Expected Equipment Uncertainty

- `Schleuniger wire cutter/stripper` and `Komax cut/strip machine` are likely wire prep equipment for work center `2100`, but exact PN/op assignment is not proven.
- `Daniels crimp press` and `Molex crimp applicator bench` are likely termination equipment for work center `2200`, but exact PN/op assignment is not proven.
- `Solder station` and `Heat gun station` are likely solder/sleeve/heat-shrink equipment for work center `2300`.
- `Hipot tester` is possible/conditional because not every harness gets hipot.
- `Ultrasonic welder` is unmapped because no ultrasonic weld operation appears.
- `Obsolete hand crimper` is incomplete/ambiguous.
