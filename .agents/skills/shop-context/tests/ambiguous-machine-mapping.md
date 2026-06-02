# Ambiguous Machine Mapping

Synthetic messy CSV-style input for ShopContext V1 validation. This file is designed to trigger user review and low/unknown confidence mappings.

## Router-Like Export

```csv
operation_number,operation_name,work_center,user_note
010,Assembly,2000,manual assembly area
020,Process,2100,coating or bonding process unclear
030,Inspect,2200,visual inspection
040,Test,,test step exported without work center
050,Reflow,2300,soldering process
065,Rework Repair,2400,conditional rework only
```

## Machine-List-Like Export

```csv
machine_name,machine_type,work_center,user_note
Bench A,Inspection,2200,manual inspection bench
Bench B,Inspection,2200,backup inspection bench
VAC 545,Vapor Phase,2300,reflow solder
Legacy Reflow Oven,Reflow,9999,old oven listed in assets
Bond Station,Bonding,2100,used for some bonding operations
Coat Booth,Coating,2100,used for coating process
Test Rack,Functional Test,,used for functional testing
Unused Press,Press,7777,no clear matching operation
```

## Expected ShopContext Notes

- Assign confidence per mapping row.
- Use Low or Unknown confidence where appropriate.
- Use `No dedicated machine identified` when a manual operation lacks a supported machine.
- List multiple candidate machines instead of choosing one without support.
- Create targeted open questions.
- Do not invent clean work center names from numeric codes.
- Do not treat numeric work center match alone as proof of mapping.
- Do not treat generic operation names as enough evidence for a High-confidence mapping.
- Preserve Op 040 missing work center as `Unknown`.
- Preserve Test Rack missing work center as `Unknown`.
- Preserve Op 065 `Rework Repair` as a conditional route role unless confirmed standard.
- Keep Unused Press visible as an unmapped machine.

## Expected Mapping Confidence Examples

| Operation # | Operation Name | Work Center | Suggested Machine | Mapping Basis | Confidence | Needs User Review? |
|---|---|---|---|---|---|---|
| 010 | Assembly | 2000 | No dedicated machine identified | Manual operation from user note; no supported machine | Low | Yes |
| 020 | Process | 2100 | Bond Station / Coat Booth | Same work center but generic operation name and two possible processes | Low | Yes |
| 030 | Inspect | 2200 | Bench A / Bench B | Same work center with multiple candidate benches | Low | Yes |
| 040 | Test | Unknown | Test Rack | Machine type and note suggest test, but both operation and machine data are incomplete | Low | Yes |
| 050 | Reflow | 2300 | VAC 545 / Legacy Reflow Oven | One direct work center match and one asset-list candidate with conflicting work center | Low | Yes |
| 065 | Rework Repair | 2400 | No mapping found | Conditional route role and no supported machine | Unknown | Yes |

## Expected Open Questions

- Does Op 030 Inspect use Bench A, Bench B, both benches, or no dedicated bench?
- Does Op 050 Reflow use VAC 545, Legacy Reflow Oven, or another soldering process?
- What does work center 2200 represent in this shop?
- Is Op 065 Rework Repair a conditional route or part of the standard flow?
- Does Op 020 Process refer to bonding, coating, both, or another process?

