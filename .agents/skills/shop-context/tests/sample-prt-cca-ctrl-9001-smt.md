# Sample PRT CCA CTRL 9001 SMT

Synthetic PRT / work instruction for `CCA-CTRL-9001 Rev A`. This file is intentionally noisy and contains a direct contradiction with the old router note.

## Document Control

```text
Document: WI-CCA-CTRL-9001-SMT
Part: CCA-CTRL-9001 Rev A
Title: SMT Build, Wash, Bake, Inspect, and Test
Revision Note: Rev A restored wash and bake after flux residue review.
Related Router Operations: 0100, 0200, 0300, 0350, 0400, 0500, 0600
```

## General Safety / ESD Notes

- Wear wrist strap and heel straps when handling bare boards.
- Verify ESD monitor is green before starting.
- Do not touch solderable surfaces with bare hands.
- Operator signoffs are required after SMT, wash, bake unload, inspection, and test.
- If this document conflicts with an old router note, use the current released PRT and notify Manufacturing Engineering.

## Op 0100 - Kit

- Pull bare boards, solder paste, components, stencil, and traveler.
- Verify paste lot is released for production.
- Verify kit count before SMT setup.

## Op 0200 - SMT Process

- Load stencil in `DEK Horizon`.
- Print solder paste using released paste program.
- Load placement program on `MY200`.
- Place SMT components.
- Run board through `VAC 545` vapor phase reflow using current SAC305 recipe.
- Inspect for missing parts, skewed parts, tombstones, and solder bridges before wash.

## Op 0300 - Wash

- Run board through `Aqueous Washer AW-3`.
- Use standard CCA wash cycle.
- Verify no visible residue remains around fine-pitch devices.

## Op 0350 - Bake

- Bake boards at 90°C for 45 minutes after wash.
- Record bake load and unload time on traveler.
- Do not proceed to inspection until boards are cool enough to handle.

## Op 0400 - Inspect

- Perform AOI review on secondary and primary SMT areas.
- Manually review AOI calls before accepting the board.
- Escalate solder bridge, missing part, and polarity findings to lead.

## Op 0500 - E-Test

- Run released functional electrical test.
- Record pass/fail status on traveler.

## Op 0600 - Final Inspection

- Final visual inspection for workmanship, cleanliness, labels, and documentation completeness.
- Verify traveler signoffs are complete.

## Footer Noise

```text
Printed copies are uncontrolled.
Old router note "No wash required" is obsolete for CCA-CTRL-9001 Rev A.
Page 1 of 4
```

## Expected ShopContext Notes

- Detect that the router note says no wash required while this PRT says wash and bake are required.
- Use shop notes and PRT content to indicate wash is required for `CCA-CTRL-9001`, while preserving the source conflict.
- Do not erase the conflict from final context.
- Include bake load/unload time and pass/fail status only as confirmed records/logs because the PRT explicitly requires them.
