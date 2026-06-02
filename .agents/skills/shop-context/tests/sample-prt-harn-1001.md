# Sample PRT HARN-1001

Synthetic PRT / work instruction for `HARN-1001 Rev A`.

## Header

```text
Document: PRT-HARN-1001-A
Part: HARN-1001 Rev A
Title: Harness Build Traveler
Revision Note: Rev A initial release.
```

## General Notes

- Follow ESD handling rules when connectors contain protected electronics.
- Wear eye protection when using heat gun and cutting tools.
- Keep wire labels legible throughout build.
- Operator signoff required at each operation.

## Op 0100 - Kit Material

- Pull wire, connector, terminal, sleeve, and label kit.
- Verify connector part numbers against BOM.
- Verify wire colors and gauges before release.
- Sign traveler after kit verification.

## Op 0200 - Wire Prep

- Cut wires to released cut sheet.
- Strip insulation to listed strip length.
- Keep cut wires bundled by circuit ID.
- Verify first-piece length before continuing lot.

## Op 0300 - Crimp Contacts

- Set up crimp press with released applicator.
- Crimp contacts to prepared leads.
- Pull-test sample crimps per traveler instruction.
- Inspect crimp height and insulation support visually.

## Op 0400 - Apply Heat Shrink

- Slide heat shrink over terminated leads where specified.
- Shrink with controlled heat gun.
- Verify tubing is centered over termination area.
- Do not scorch insulation.

## Op 0500 - Layout Harness

- Lay harness on board.
- Route branches per board pins.
- Tie/lace harness at indicated stations.
- Verify branch lengths before removing from board.

## Op 0600 - Continuity Test

- Connect harness to continuity tester.
- Run released continuity program for `HARN-1001`.
- Resolve open/short indications before final inspection.

## Op 0700 - Final Inspection

- Perform final visual inspection.
- Verify labels, connector orientation, branch lengths, tie/lace locations, and heat shrink position.
- Record accepted/rejected status on traveler.

## Op 0800 - Pack

- Coil harness without kinking.
- Bag with protective caps on connectors.
- Close traveler after pack.
