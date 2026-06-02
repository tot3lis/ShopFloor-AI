# Sample Router Bad Input Quality

Synthetic messy router / work-order export for ShopContext validation. This fixture is public-safe and intentionally contains incomplete, contradictory, and duplicated information.

The purpose of this package is to validate that ShopContext can handle poor manufacturing input quality without inventing clean mappings or producing a bloated final reference.

## Router Export

```csv
wo,part_number,revision,seq,op_no,operation_name,work_center,attached_doc,user_note
WO-CTRL-9001-A,CCA-CTRL-9001,A,10,0100,Kit Material,1000,WI-CCA-CTRL-9001-SMT.pdf,Kit board, paste, and SMT components
WO-CTRL-9001-A,CCA-CTRL-9001,A,20,0200,SMT Process,2110,WI-CCA-CTRL-9001-SMT.pdf,No wash required per old note
WO-CTRL-9001-A,CCA-CTRL-9001,A,30,0300,Wash,2150,WI-CCA-CTRL-9001-SMT.pdf,See PRT if wash applies
WO-CTRL-9001-A,CCA-CTRL-9001,A,35,0350,Bake / Dry,2160,WI-CCA-CTRL-9001-SMT.pdf,Bake after wash when required
WO-CTRL-9001-A,CCA-CTRL-9001,A,40,0400,Inspect,2210,WI-CCA-CTRL-9001-SMT.pdf,AOI review
WO-CTRL-9001-A,CCA-CTRL-9001,A,50,0500,E-Test,3100,WI-CCA-CTRL-9001-SMT.pdf,Functional electrical test
WO-CTRL-9001-A,CCA-CTRL-9001,A,60,0600,Final Inspection,4100,WI-CCA-CTRL-9001-SMT.pdf,Final visual inspection
WO-CTRL-9002-B,CCA-CTRL-9002,B,10,0100,Material Kit,1000,WI-CCA-9002-SMT.docx,Material pull
WO-CTRL-9002-B,CCA-CTRL-9002,B,20,0200,Process Board,2110,WI-CCA-9002-SMT.docx,Vague SMT operation; instruction not uploaded
WO-CTRL-9002-B,CCA-CTRL-9002,B,30,0300,Clean,2150,WI-CCA-9002-SMT.docx,Clean board if required
WO-CTRL-9002-B,CCA-CTRL-9002,B,40,0400,Inspect,2210,WI-CCA-9002-SMT.docx,Inspection step 1
WO-CTRL-9002-B,CCA-CTRL-9002,B,45,0450,Inspect,4100,WI-CCA-9002-SMT.docx,Inspection step 2; unclear AOI vs manual visual
WO-CTRL-9002-B,CCA-CTRL-9002,B,50,0500,Electrical Test,3100,WI-CCA-9002-SMT.docx,E-test
WO-PWR-9010-C,CCA-PWR-9010,C,10,0010,Stock Issue,1000,WI-CCA-PWR-9010-PRT.pdf,Kit issue from stores
WO-PWR-9010-C,CCA-PWR-9010,C,20,0020,Build SMT,2110,WI-CCA-PWR-9010-PRT.pdf,SMT build with vague PRT headers
WO-PWR-9010-C,CCA-PWR-9010,C,25,0250,Clean / Bake,,WI-CCA-PWR-9010-PRT.pdf,Work center blank in export
WO-PWR-9010-C,CCA-PWR-9010,C,30,0300,AOI Check,2210,WI-CCA-PWR-9010-PRT.pdf,AOI or visual per PRT
WO-PWR-9010-C,CCA-PWR-9010,C,40,0400,Coat,1700,WI-CCA-PWR-9010-PRT.pdf,Conformal coat required
WO-PWR-9010-C,CCA-PWR-9010,C,50,0500,Test,3100,WI-CCA-PWR-9010-PRT.pdf,Electrical test
WO-PWR-9010-C,CCA-PWR-9010,C,60,0600,Closeout,9000,WI-CCA-PWR-9010-PRT.pdf,Final paperwork and pack
```

## Bad Input Features

- `CCA-CTRL-9001` router note says `No wash required per old note`, but the uploaded PRT says wash and bake are required.
- `CCA-CTRL-9002` references `WI-CCA-9002-SMT.docx`, but that instruction is intentionally not included in this package.
- `CCA-CTRL-9002` has repeated inspection operations: `0400 Inspect` and `0450 Inspect`, with unclear difference.
- `CCA-PWR-9010` uses messy operation numbers `0010`, `0020`, and `0250`.
- `CCA-PWR-9010` operation `0250 Clean / Bake` has a blank work center.
- `CCA-PWR-9010` PRT headers are intentionally unclear and do not exactly match router operation names.
- Operation names are inconsistent across part numbers: `SMT Process`, `Process Board`, `Build SMT`, `E-Test`, `Electrical Test`, and `Test`.

## Expected ShopContext Notes

- Preserve operation numbers exactly, including `0010`, `0020`, and `0250`.
- Preserve blank work center as `Unknown`.
- Do not invent internal steps for missing `WI-CCA-9002-SMT.docx`.
- Detect and preserve the source conflict around wash requirements for `CCA-CTRL-9001`.
- Preserve repeated inspection operations for `CCA-CTRL-9002` instead of merging them without support.
