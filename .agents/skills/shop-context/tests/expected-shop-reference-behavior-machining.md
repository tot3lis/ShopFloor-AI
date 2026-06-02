# Expected Shop Reference Behavior - Machining

This file describes expected ShopContext behavior for the machining / precision metal fabrication edge-case package:

- `sample-router-machining-shared-wo.md`
- `sample-prt-machining-multi-op-instruction.md`
- `sample-machine-list-machining-unmapped.md`
- `sample-shop-notes-machining.md`

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

- Recognize the shop as machining / precision metal fabrication.
- Preserve operation numbers exactly: `0100`, `0200`, `0300`, `0400`, `0500`, `0600`, `0700`.
- Preserve operation names exactly, including inconsistent terms such as `Machine 1st Side`, `2nd Op Machine`, `Deburr`, `Chem Film`, and `Final Insp`.
- Preserve work center codes exactly: `1000`, `2200`, `2300`, `2400`, `3100`, `9000`.
- Handle the same WO/traveler number `WO-MACH-44591` being reused across multiple operations.
- Recognize that `sample-prt-machining-multi-op-instruction.md` is one document containing multiple operation instruction sections.
- Split the PRT into operation-specific step summaries by operation header.
- Do not copy the full PRT into final `shop-reference.md`.
- Do not treat the whole PRT as one operation.
- Do not require the machine list to explicitly map machines to operation numbers.
- Infer likely machines/tools from operation headers, instruction content, work centers, and machine types when supported.
- Use uncertainty wording where exact machine assignment is not proven, especially for the CNC mill used by Ops `0200` and `0300`.
- Preserve exact instruction terms such as `M-12`, `FX-BRKT-782-A`, `FX-BRKT-782-B`, `BRKT782_SIDE1_REV-C`, and `BRKT782_SIDE2_REV-C`.
- Include manual work such as deburr and closeout inside Operation Step Summaries, not as a standalone final section.
- Include inspection and acceptance context inside Operation Step Summaries and Quality Gates.
- Include confirmed traveler signoffs and final acceptance only where explicitly supported.
- Do not create a generic Evidence Sources / Likely Records To Check section.
- Do not include Open Questions in the final `shop-reference.md`.
- Combine alternate terms and ambiguous language into `Shop-Specific Language`.
- Do not perform RCCA, root cause analysis, corrective action, trend analysis, SPC analysis, machine performance analysis, maintenance analysis, dynamic data integration, or larger-system routing.

## Expected Uncertainty Handling

- `Haas VF-2SS CNC Mill` and `Haas VF-4 CNC Mill` are possible CNC resources for work center `2200`, but the PRT names `M-12` and the machine list does not identify which listed machine is `M-12`.
- `CMM Zeiss Contura` may support final inspection when a dimensional report is required, but the shop notes say not every job requires CMM.
- `Laser Marking Station` should remain unmapped because the router has no laser marking operation.
- `Old Bridgeport Mill` should remain ambiguous/incomplete because the asset ID and work center are missing.
