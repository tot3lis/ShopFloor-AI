# Sample PRT Machining Multi-Op Instruction

Synthetic copied PRT / traveler / manufacturing instruction for ShopContext validation. This file simulates a single PDF or Word document copied into markdown. It intentionally contains multiple operation instruction sections in one document.

## Document Control

```text
Document: PRT-AL-BRACKET-782-C
Title: Manufacturing Process Routing Traveler - AL-BRACKET-782 Rev C
WO / Traveler: WO-MACH-44591
Part: AL-BRACKET-782 Rev C
Material: 6061-T6 aluminum
Owner: Manufacturing Engineering
Revision Note: Rev C updates second-side counterbore depth and chem film masking note.
```

## General Shop Notes

- Follow current EHS and PPE requirements for machining chips, coolant, and chem film handling.
- Keep traveler with the lot at all times.
- Do not mix parts from another WO in the same tray.
- Use soft jaws or approved fixture surfaces only.
- Remove sharp chips before moving parts to inspection.
- Operator and inspector signoff blocks appear after each operation section.
- Repeated generic note: verify traveler number before starting work.

## Op 0100 - Material Issue

- Pull 6061-T6 aluminum blank from approved stock.
- Verify material cert matches `6061-T6`.
- Verify blank size before release to CNC.
- Stamp traveler after material verification.

Signoff:

```text
Material Handler Initials: ______
Date: ______
```

## Op 0200 - Machine First Side

Setup notes:

- Load part into CNC Mill `M-12`.
- Use fixture `FX-BRKT-782-A`.
- Verify tool list against setup sheet loaded at the machine.
- Confirm coolant concentration is within posted shop range before cutting.

Run notes:

- Run program `BRKT782_SIDE1_REV-C`.
- Rough mill outside profile.
- Face top surface.
- Drill mounting holes.
- Chamfer top edges.
- In-process inspect datum A and hole pattern before removing from fixture.

Signoff:

```text
Operator Initials: ______
In-Process Inspector: ______
```

## Op 0300 - Machine Second Side

Setup notes:

- Flip part into fixture `FX-BRKT-782-B`.
- Confirm datum A is seated before clamp.
- Run program `BRKT782_SIDE2_REV-C`.

Run notes:

- Finish mill backside pocket.
- Drill and countersink remaining holes.
- Break chips before final pass if chatter appears.
- Verify thickness.
- In-process inspect flatness before release to deburr.

Signoff:

```text
Operator Initials: ______
In-Process Inspector: ______
```

## Op 0400 - Deburr / Edge Break

- Hand deburr all machined edges.
- Scotch-Brite visible tool marks only where allowed by drawing notes.
- Do not round datum edges.
- Verify no loose chips remain in holes or pocket.
- Keep threaded features protected during deburr.

Signoff:

```text
Deburr Operator: ______
```

## Op 0500 - Chem Film / Alodine

- Send to chem film area.
- Mask threaded inserts if present.
- Apply Class 3 chem film per shop process.
- Rinse and dry per local chem film work instruction.
- Verify no pooling or bare aluminum in required coverage areas.

Signoff:

```text
Chem Film Operator: ______
```

## Op 0600 - Final Inspection

- Verify dimensions per drawing.
- Verify hole pattern.
- Verify finish.
- Verify chem film coverage.
- Use CMM only when dimensional report is required by customer or inspection plan.
- Record acceptance on traveler.

Signoff:

```text
Final Inspector: ______
Accepted / Rejected: ______
```

## Op 0700 - Pack / Closeout

- Confirm all traveler signoffs are complete.
- Bag parts with protective paper between brackets.
- Attach copy of material cert when required by purchase order.
- Close WO in legacy MRP after parts are packed.

## Footer Noise

```text
Printed copies are uncontrolled.
If this document conflicts with the released drawing, stop and contact Manufacturing Engineering.
Blank signoff blocks are shown for traveler format only.
Page 1 of 6
```

## Expected ShopContext Notes

- Treat this as one PRT document containing multiple operation instruction sections.
- Split the document by operation headers instead of summarizing the whole PRT as one operation.
- Use operation headers to connect internal steps to router operations.
- Preserve exact terms such as `M-12`, `FX-BRKT-782-A`, `FX-BRKT-782-B`, `BRKT782_SIDE1_REV-C`, and `BRKT782_SIDE2_REV-C`.
- Include traveler signoff and final acceptance only as confirmed records/logs because they are explicitly present in the source.
- Do not copy the full PRT into final `shop-reference.md`.
