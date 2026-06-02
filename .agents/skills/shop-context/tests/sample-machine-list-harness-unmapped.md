# Sample Machine List Harness Unmapped

Synthetic machine/equipment list for a harness manufacturing shop. This machine list intentionally does not map equipment to operation numbers or part numbers.

## Machine / Equipment Export

```csv
asset_id,machine_name,machine_type,work_center,area,user_note
WIRE-CT-01,Schleuniger wire cutter/stripper,Wire Cut/Strip Machine,2100,Wire Prep,Programmable cut and strip equipment
WIRE-CT-02,Komax cut/strip machine,Wire Cut/Strip Machine,2100,Wire Prep,Alternate cut/strip equipment
CRIMP-01,Daniels crimp press,Crimp Press,2200,Termination,Crimp press for applicator tooling
CRIMP-02,Molex crimp applicator bench,Crimp Bench,2200,Termination,Bench applicator setup
SOLD-03,Solder station,Solder Station,2300,Solder / Sleeve,Solder splice station
HEAT-02,Heat gun station,Heat Tool,2300,Solder / Sleeve,Controlled heat gun station
BOARD-04,Harness layout board table,Layout Board,2400,Harness Assembly,Layout and tie/lace station
TEST-07,Continuity tester,Continuity Tester,3100,Electrical Test,Continuity test equipment
TEST-09,Hipot tester,Hipot Tester,3100,Electrical Test,Hipot capability; not every harness uses hipot
INSP-02,Final inspection bench,Inspection Bench,4100,Final Inspection,Final visual inspection station
LBL-01,Label printer,Label Printer,9000,Pack / Closeout,Label printing for packaging and traveler closeout
WELD-01,Ultrasonic welder,Ultrasonic Welder,,Weld,No matching router operation in this sample package
,Obsolete hand crimper,Hand Crimper,,Termination,Incomplete export row; unclear if active
```

## Expected ShopContext Notes

- Preserve machine names, asset IDs, and work centers exactly.
- Do not invent operation-number mappings from this list.
- Infer likely equipment context from machine type, work center, and PRT content only where supported.
- Treat `Hipot tester` as possible/conditional because shop notes say not every harness gets hipot.
- Keep `Ultrasonic welder` visible as unmapped because no ultrasonic weld operation appears.
- Mark `Obsolete hand crimper` as incomplete/ambiguous with `Unknown` work center.
