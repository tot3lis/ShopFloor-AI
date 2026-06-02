# Sample Machine List Realistic

Synthetic machine/equipment export for ShopContext validation. This file is intentionally imperfect and public-safe.

## Machine / Equipment Export

```csv
asset_id,machine_name,machine_type,work_center,area,user_note
SMT-PRN-014,DEK Horizon,Stencil Printer,2110,Secondary SMT,Used for paste print on secondary and primary side jobs
SMT-PNP-022,MY200,Pick-and-Place,2110,Secondary SMT,Main SMT placement platform for CCA-PSU products
SMT-VP-003,VAC 545,Vapor Phase Reflow,2110,SMT Reflow,VP reflow for SAC305 assemblies
WASH-003,Aqueous Washer AW-3,Board Washer,2150,Wash,Standard CCA wash cycle equipment
OVEN-090,Blue M Bake Oven,Bake Oven,2160,Bake,Used for 90C post-wash bake when required by instruction
AOI-221,Koh Young Zenith,AOI,2210,Inspection,Secondary side AOI review station
TEST-310-E,Electrical Test Station ETS-7,Functional Test,3100,Electrical Test,Runs released CCA functional test scripts
VIS-410-B,Final Visual Bench B,Inspection Bench,4100,Final QA,Backup final inspection bench
COAT-170-1,Conformal Coat Booth,Coating,1700,Coating,No matching operation in this sample router
,Spare Hot Plate,Hot Plate,,SMT Support,Incomplete export row; unclear current use
```

## Expected ShopContext Notes

- Preserve machine names and asset IDs exactly.
- Preserve numeric work centers exactly.
- Mark the empty work center for `Spare Hot Plate` as `Unknown`.
- Map `DEK Horizon`, `MY200`, `VAC 545`, `Aqueous Washer AW-3`, and `Blue M Bake Oven` to internal steps inside operation `0200` when combined with the attached work instruction.
- Map `Koh Young Zenith` to `0300 Inspect Secondary Side` or AOI-related quality gates when supported.
- Map `Electrical Test Station ETS-7` to `0500 E-Test`.
- Keep `Conformal Coat Booth` visible as unmapped because no coating operation appears in the sample router.
- Treat `Spare Hot Plate` as ambiguous/unmapped.
- Do not create generic logs or evidence sources from machine type alone.
