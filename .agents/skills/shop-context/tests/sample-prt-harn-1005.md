# Sample PRT HARN-1005

Synthetic PRT / work instruction for `HARN-1005 Rev D`.

## Header

```text
Document: PRT-HARN-1005-D
Part: HARN-1005 Rev D
Revision Note: Legacy operation names retained from prior system.
```

## General Notes

- `Process Leads` is a legacy operation label.
- Do not proceed to test until all lead processing checks are complete.
- Operator signoff required after lead processing and test.

## Op 0100 - Stock Issue

- Issue wire, terminals, solder sleeves, heat shrink, connector parts, and labels.
- Verify stock lot against traveler.

## Op 0200 - Lead Prep

- Cut leads to length.
- Strip insulation.
- Verify strip length and check for strand damage.

## Op 0300 - Process Leads

- Verify stripped leads are ready for termination.
- Crimp contacts where specified.
- Solder splice where specified.
- Apply sleeve over splice or termination area.
- Heat shrink sleeve with controlled heat gun.
- Pull-test sample crimps.
- Inspect for exposed conductor and sleeve position.

## Op 0400 - Harness Build

- Lay harness on board.
- Install connectors and route branches.
- Tie/lace harness at specified positions.

## Op 0500 - Test

- Run continuity test.
- Verify no opens or shorts.
- Hipot only if called out by customer test note.

## Op 0600 - Inspect / Pack

- Final visual inspection.
- Verify labels, connector seating, sleeve coverage, branch lengths, and packaging.
- Bag harness and close traveler.
