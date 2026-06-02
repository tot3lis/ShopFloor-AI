# Sample Router Harness Five PNs

Synthetic messy router / work-order exports for ShopContext validation. This fixture is public-safe and does not represent real production data.

The purpose of this package is to validate that ShopContext can compare multiple cable / harness part numbers with similar flows, inconsistent operation naming, and different operation granularity.

## Router Export

```csv
wo,part_number,revision,seq,op_no,operation_name,work_center,attached_doc,user_note
WO-HARN-1001-A,HARN-1001,A,10,0100,Kit Material,1000,PRT-HARN-1001-A.pdf,Pull wire and connector kit
WO-HARN-1001-A,HARN-1001,A,20,0200,Wire Prep,2100,PRT-HARN-1001-A.pdf,Cut and strip per cut sheet
WO-HARN-1001-A,HARN-1001,A,30,0300,Crimp Contacts,2200,PRT-HARN-1001-A.pdf,Terminate crimp contacts
WO-HARN-1001-A,HARN-1001,A,40,0400,Apply Heat Shrink,2300,PRT-HARN-1001-A.pdf,Heat shrink separate from crimp
WO-HARN-1001-A,HARN-1001,A,50,0500,Layout Harness,2400,PRT-HARN-1001-A.pdf,Board layout and lace
WO-HARN-1001-A,HARN-1001,A,60,0600,Continuity Test,3100,PRT-HARN-1001-A.pdf,Electrical continuity
WO-HARN-1001-A,HARN-1001,A,70,0700,Final Inspection,4100,PRT-HARN-1001-A.pdf,Final visual
WO-HARN-1001-A,HARN-1001,A,80,0800,Pack,9000,PRT-HARN-1001-A.pdf,Pack and close
WO-HARN-1002-B,HARN-1002,B,10,0100,Material Issue,1000,PRT-HARN-1002-B.pdf,Kit issue
WO-HARN-1002-B,HARN-1002,B,20,0200,Cut / Strip,2100,PRT-HARN-1002-B.pdf,Combined cut-strip
WO-HARN-1002-B,HARN-1002,B,30,0300,Terminate / Sleeve Leads,2200,PRT-HARN-1002-B.pdf,Combined termination and sleeve
WO-HARN-1002-B,HARN-1002,B,40,0400,Harness Assembly,2400,PRT-HARN-1002-B.pdf,Board build
WO-HARN-1002-B,HARN-1002,B,50,0500,E-Test,3100,PRT-HARN-1002-B.pdf,Continuity test in older route
WO-HARN-1002-B,HARN-1002,B,60,0600,Final Insp,4100,PRT-HARN-1002-B.pdf,Final inspection
WO-HARN-1002-B,HARN-1002,B,70,0700,Closeout,9000,PRT-HARN-1002-B.pdf,Close work order
WO-HARN-1003-C,HARN-1003,C,10,0100,Kit,1000,PRT-HARN-1003-C.pdf,Material kit
WO-HARN-1003-C,HARN-1003,C,20,0200,Cut Wires,2100,PRT-HARN-1003-C.pdf,Cut only
WO-HARN-1003-C,HARN-1003,C,25,0250,Strip Leads,2100,PRT-HARN-1003-C.pdf,Strip after cut
WO-HARN-1003-C,HARN-1003,C,30,0300,Install Terminals,2200,PRT-HARN-1003-C.pdf,Crimp/install terminals
WO-HARN-1003-C,HARN-1003,C,40,0400,Solder Splices,2300,PRT-HARN-1003-C.pdf,Solder splice operation
WO-HARN-1003-C,HARN-1003,C,50,0500,Sleeve,2300,PRT-HARN-1003-C.pdf,Sleeve over splice
WO-HARN-1003-C,HARN-1003,C,60,0600,Buzz Out,3100,PRT-HARN-1003-C.pdf,Continuity language from legacy traveler
WO-HARN-1003-C,HARN-1003,C,70,0700,Final QA,4100,PRT-HARN-1003-C.pdf,Final QA check
WO-HARN-1004-A,HARN-1004,A,10,0100,Kit Pull,1000,PRT-HARN-1004-A.pdf,Pull kit
WO-HARN-1004-A,HARN-1004,A,20,0200,Prep Leads,2100,PRT-HARN-1004-A.pdf,Cut and strip combined
WO-HARN-1004-A,HARN-1004,A,30,0300,Crimp / Solder,2200,PRT-HARN-1004-A.pdf,Crimp and solder by PRT
WO-HARN-1004-A,HARN-1004,A,40,0400,Insulate Splices,2300,PRT-HARN-1004-A.pdf,Sleeve/heat shrink equivalent
WO-HARN-1004-A,HARN-1004,A,50,0500,Board Layout,2400,PRT-HARN-1004-A.pdf,Harness board
WO-HARN-1004-A,HARN-1004,A,60,0600,Electrical Test,3100,PRT-HARN-1004-A.pdf,E-test wording variant
WO-HARN-1004-A,HARN-1004,A,70,0700,Final Inspection,4100,PRT-HARN-1004-A.pdf,Final inspection
WO-HARN-1005-D,HARN-1005,D,10,0100,Stock Issue,1000,PRT-HARN-1005-D.pdf,Stock issue
WO-HARN-1005-D,HARN-1005,D,20,0200,Lead Prep,2100,PRT-HARN-1005-D.pdf,Lead prep
WO-HARN-1005-D,HARN-1005,D,30,0300,Process Leads,2200,PRT-HARN-1005-D.pdf,Vague legacy op name
WO-HARN-1005-D,HARN-1005,D,40,0400,Harness Build,2400,PRT-HARN-1005-D.pdf,Board build
WO-HARN-1005-D,HARN-1005,D,50,0500,Test,3100,PRT-HARN-1005-D.pdf,Electrical test
WO-HARN-1005-D,HARN-1005,D,60,0600,Inspect / Pack,4100,PRT-HARN-1005-D.pdf,Final inspection plus pack
```

## Expected ShopContext Notes

- Preserve all part numbers, revisions, operation numbers, operation names, and work centers exactly.
- Compare operation meanings across part numbers without flattening all routes into one fake universal route.
- Recognize same-meaning naming variants such as `Wire Prep`, `Cut / Strip`, `Prep Leads`, `Lead Prep`, and the split `Cut Wires` + `Strip Leads`.
- Recognize granularity differences where one PN splits work into multiple operations and another combines the same work.
- Use the PRT for each part number to understand what actually happens inside each operation.
