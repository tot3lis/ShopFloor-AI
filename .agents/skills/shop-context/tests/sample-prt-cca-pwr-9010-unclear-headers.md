# Sample PRT CCA PWR 9010 Unclear Headers

Synthetic PRT for `CCA-PWR-9010 Rev C`. This file intentionally uses unclear section headers that do not cleanly match router operation names.

## Control Block

```text
Document: WI-CCA-PWR-9010-PRT
Part: CCA-PWR-9010 Rev C
Title: Power CCA Traveler Copy
Revision Note: Converted from legacy traveler with inconsistent headings.
```

## STEP A - MATERIAL

- Pull bare board, components, paste, wash basket, conformal coat mask, and labels.
- Verify kit against traveler.
- Keep moisture-sensitive parts sealed until SMT setup.

## 0200 SMT

- Print solder paste.
- Run pick-and-place.
- Run vapor phase reflow.
- Use current power-board SMT program.
- Inspect for obvious placement errors before cleaning.

## Clean Bake Step

- Wash board after reflow.
- Bake after wash until dry per local bake instruction.
- Header does not show an operation number, but router has `0250 Clean / Bake` with blank work center.

## VISUAL CHECK

- Perform AOI review if program is available.
- If AOI program is not available, perform manual visual inspection.
- Check polarity, solder bridges, missing parts, and wash residue.

## COATING

- Mask connector mating surfaces.
- Apply conformal coat.
- Verify coverage and keep-out areas.

## TEST AREA

- Run electrical test.
- Record pass/fail on traveler.

## FINAL

- Verify labels and coating cure status.
- Verify traveler is complete.
- Pack board with ESD bag and closeout paperwork.

## Expected ShopContext Notes

- Infer probable operation matching from headers and content, but use uncertainty wording because headers are inconsistent.
- Probable matches:
  - `STEP A - MATERIAL` to router `0010 Stock Issue`
  - `0200 SMT` to router `0020 Build SMT`
  - `Clean Bake Step` to router `0250 Clean / Bake`
  - `VISUAL CHECK` to router `0300 AOI Check`
  - `COATING` to router `0400 Coat`
  - `TEST AREA` to router `0500 Test`
  - `FINAL` to router `0600 Closeout`
- Preserve uncertainty and do not claim exact matching is proven.
