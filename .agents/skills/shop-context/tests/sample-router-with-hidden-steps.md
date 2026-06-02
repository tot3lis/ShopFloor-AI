# Sample Router With Hidden Steps

Synthetic messy work-order/router export for ShopContext validation. This is public-safe test data and does not represent a real shop order.

The purpose of this fixture is to validate that ShopContext treats the router as the operation label and sequence source, while using attached operation instructions to understand the real internal process steps.

## Work Order Header

```text
WO: WO-CCA-77821
Assembly: CCA-PSU-CTRL-A2
Revision: G
Qty: 18
Route Name: CCA SECONDARY/PRIMARY BUILD - MIXED EXPORT
Planner Note: Some operation descriptions are legacy names. See attached instructions where listed.
```

## Router / Operation Export

```csv
seq,op_no,operation_name,work_center,resource_group,attached_instruction,user_note
10,0100,Kit Material,1000,STORES,,Pull kit, verify ESD bags, issue controlled solder paste if required
20,0200,Process Secondary Side,2110,SMT SEC,WI-CCA-0200-SEC-SIDE Rev C.pdf,Legacy op name; includes multiple substeps
30,0300,Inspect Secondary Side,2210,AOI / VISUAL,,AOI review after secondary side process
40,0400,Primary Side Process,2110,SMT PRI,WI-CCA-0400-PRIMARY.docx,Name differs from old router: Process Primary Side
50,0500,E-Test,3100,TEST-RACK,,Functional electrical test; sometimes written Electrical Test
60,0600,Final Inspection,4100,QA FINAL,,Final visual buyoff and paperwork review
```

## Messy Export Notes

- Operation `0200` is intentionally vague. The router does not reveal the internal process steps.
- Operation `0400` uses inconsistent naming: `Primary Side Process` in this export, but the planner note says older routers may call it `Process Primary Side`.
- Operation `0500` uses the short name `E-Test`; shop notes may call the same operation `Electrical Test`.
- Preserve operation numbers exactly as shown, including leading zeroes.
- Preserve numeric work centers exactly: `1000`, `2110`, `2210`, `3100`, `4100`.
- Treat attached instruction references as links to process detail, not as proof that a specific unit completed the operation.

## Expected ShopContext Notes

- Use the router for operation sequence and labels.
- Do not assume `0200 Process Secondary Side` is atomic.
- Link `WI-CCA-0200-SEC-SIDE Rev C.pdf` to operation `0200` when the corresponding copied instruction is provided.
- Keep operation `0400 Primary Side Process` visible even if no primary-side instruction is provided in this package.
- Mark missing details for `0400` as unresolved during review, not as invented process steps.
- Preserve inconsistent shop names and normalize their likely meaning separately.
