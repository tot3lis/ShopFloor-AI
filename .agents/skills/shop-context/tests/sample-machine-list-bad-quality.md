# Sample Machine List Bad Quality

Synthetic messy machine/equipment export. This file intentionally contains duplicates, conflicts, missing fields, stale equipment, and inconsistent naming.

## Machine / Equipment Export

```csv
asset_id,machine_name,machine_type,work_center,status,user_note
SMT-PRN-014,DEK Horizon,Stencil Printer,2110,active,Primary stencil printer name in asset system
SMT-PRN-014,DEK Horizon 03,Stencil Printer,2110,active,Alternate exported name for same printer
SMT-PNP-022,MY200,Pick-and-Place,2110,active,Main SMT placement platform
,MY-200 PNP,Pick-and-Place,2110,active,Name variant from old export; asset blank
SMT-VP-003,VAC 545,Vapor Phase Reflow,2110,active,VP oven name from maintenance list
SMT-VP-003,Vapor Phase Oven,Vapor Phase Reflow,2120,active,Same asset appears with conflicting work center
WASH-003,Aqueous Washer AW-3,Board Washer,,active,Work center missing in export
OVEN-090,Blue M Bake Oven,Bake Oven,2160,active,Bake oven
AOI-221,Koh Young AOI,AOI,2210,active,AOI system name from inspection list
,AOI Review Station,AOI Review,2210,active,Generic station name, asset blank
WASH-001,Old Washer Line,Board Washer,2150,retired,Retired washer line
COAT-170-1,Conformal Coat Booth,Coating,1700,active,Coating booth
TEST-310-E,Electrical Test Station,Functional Test,3100,active,Electrical functional test station
```

## Expected ShopContext Notes

- Identify likely duplicate/alias pairs without silently collapsing them:
  - `DEK Horizon` and `DEK Horizon 03`
  - `MY200` and `MY-200 PNP`
  - `VAC 545` and `Vapor Phase Oven`
- Preserve conflicting work center values `2110` and `2120` for vapor phase asset `SMT-VP-003`.
- Preserve missing work center for `Aqueous Washer AW-3` as `Unknown`.
- Mark `Old Washer Line` as retired/stale and do not treat it as active equipment.
- Do not invent operation-number mappings from this machine list.
