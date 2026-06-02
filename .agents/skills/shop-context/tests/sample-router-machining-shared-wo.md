# Sample Router Machining Shared WO

Synthetic messy router / work-order export for ShopContext validation. This is public-safe test data and does not represent a real shop order.

The purpose of this fixture is to validate that ShopContext can handle a machining / precision metal fabrication route where the same WO/traveler number is reused across multiple operations, operation names are inconsistent, and detailed internal steps live outside the router.

## Work Order Header

```text
WO / Traveler: WO-MACH-44591
Part: AL-BRACKET-782 Rev C
Material: 6061-T6 aluminum
Qty: 42
Router Export: LEGACY_MRP_ROUTER_V7
Planner Note: One traveler covers all operations. Details are in attached PRT instruction.
```

## Router / Work Order Export

```csv
wo_traveler,seq,op_no,operation_name,work_center,dept,attached_doc,user_note
WO-MACH-44591,10,0100,Material Issue,1000,STORES,PRT-AL-BRACKET-782-C.pdf,Pull material and start traveler
WO-MACH-44591,20,0200,Machine 1st Side,2200,CNC MILL,PRT-AL-BRACKET-782-C.pdf,Also called Machine First Side on some routers
WO-MACH-44591,30,0300,2nd Op Machine,2200,CNC MILL,PRT-AL-BRACKET-782-C.pdf,Second side machining; name shortened in export
WO-MACH-44591,40,0400,Deburr,2300,FINISH,PRT-AL-BRACKET-782-C.pdf,Edge Break sometimes shown as separate line
WO-MACH-44591,50,0500,Chem Film,2400,SURFACE TREAT,PRT-AL-BRACKET-782-C.pdf,Older orders may say Alodine
WO-MACH-44591,60,0600,Final Insp,3100,INSPECTION,PRT-AL-BRACKET-782-C.pdf,Final Inspection
WO-MACH-44591,70,0700,Pack / Closeout,9000,SHIP / CLOSE,PRT-AL-BRACKET-782-C.pdf,Close traveler and pack parts
```

## Messy Export Notes

- `WO-MACH-44591` is intentionally repeated on every operation line.
- The repeated WO/traveler number should not cause ShopContext to merge all operations into one step.
- Operation names are inconsistent with common shop language:
  - `Machine 1st Side` may also be called `Machine First Side`.
  - `2nd Op Machine` means second-side machining.
  - `Deburr` may be called `Deburr / Edge Break` or `Edge Break`.
  - `Chem Film` may be called `Alodine`.
  - `Final Insp` means `Final Inspection`.
- Preserve operation numbers exactly as shown.
- Preserve numeric work centers exactly: `1000`, `2200`, `2300`, `2400`, `3100`, `9000`.
- Do not infer detailed internal process steps from this router alone.

## Expected ShopContext Notes

- Use this router for operation labels, sequence, work centers, and repeated traveler context.
- Use the shared attached PRT instruction to split internal process details by operation header.
- Do not treat `PRT-AL-BRACKET-782-C.pdf` as one giant instruction for the entire route.
- Do not collapse all operations just because they share `WO-MACH-44591`.
