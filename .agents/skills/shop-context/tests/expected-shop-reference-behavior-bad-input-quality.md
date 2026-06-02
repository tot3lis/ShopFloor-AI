# Expected Shop Reference Behavior - Bad Input Quality

This file describes expected ShopContext behavior for the bad-input-quality CCA/electronics package:

- `sample-router-bad-input-quality.md`
- `sample-prt-cca-ctrl-9001-smt.md`
- `sample-prt-cca-pwr-9010-unclear-headers.md`
- `sample-machine-list-bad-quality.md`
- `sample-shop-notes-bad-quality.md`

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

- Recognize the shop as CCA/electronics assembly.
- Handle missing PRT for `CCA-CTRL-9002`.
- Do not fabricate internal steps for missing `WI-CCA-9002-SMT.docx`.
- Handle unclear PRT headers for `CCA-PWR-9010` using uncertainty wording.
- Detect the router-vs-PRT contradiction for `CCA-CTRL-9001` wash requirement.
- Use shop notes to resolve that wash is required for `CCA-CTRL-9001`, while preserving the source conflict.
- Handle duplicate machine names/assets without silently inventing a clean machine list.
- Mark `Old Washer Line` as retired/stale and do not treat it as active equipment.
- Handle conflicting VP work centers `2110` and `2120` without losing original values.
- Handle repeated inspection operations by preserving the ambiguity between AOI and manual visual.
- Preserve blank work centers as `Unknown`.
- Does not create fake machine-to-operation mappings from the machine list.
- Does not output a generic Evidence Sources or Likely Records To Check section.
- Does not include Open Questions in final `shop-reference.md`.
- Keeps uncertainty visible in relevant final sections where unresolved.
- Does not perform RCCA, root cause analysis, corrective action, trend analysis, SPC analysis, dynamic data integration, or larger-system routing.

## Expected Uncertainty Handling

- `CCA-CTRL-9002 0200 Process Board` remains missing detailed internal steps because `WI-CCA-9002-SMT.docx` is not uploaded.
- `CCA-PWR-9010` PRT sections are probably matchable to router operations, but the final reference should use uncertainty wording because headers are unclear.
- `CCA-CTRL-9002 0400 Inspect` and `0450 Inspect` should remain distinct or explicitly uncertain.
- `Aqueous Washer AW-3` has missing work center in the machine list.
- `VAC 545` / `Vapor Phase Oven` should preserve the `2110` / `2120` work center conflict.
