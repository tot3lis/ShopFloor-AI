# Sample Machine List Machining Unmapped

Synthetic machine/equipment export for ShopContext validation. This fixture intentionally does not map machines to operation numbers.

## Machine / Equipment Export

```csv
asset_id,machine_name,machine_type,work_center,area,user_note
CNC-012,Haas VF-2SS CNC Mill,CNC Mill,2200,CNC Milling,High-speed vertical mill
CNC-014,Haas VF-4 CNC Mill,CNC Mill,2200,CNC Milling,Larger travel vertical mill
BENCH-DB-02,Manual Deburr Bench,Deburr Bench,2300,Deburr,Hand deburr station
DBR-017,Scotch-Brite Wheel,Deburr Tool,2300,Deburr,Used for allowed surface blending only
CHEM-AL-03,Chem Film Tank Line,Chem Film Line,2400,Chem Film,Class 3 chem film process line
CMM-006,CMM Zeiss Contura,CMM,3100,Inspection,Dimensional inspection equipment
INS-HT-02,Height Gauge Station,Inspection Tool,3100,Inspection,Manual height and feature checks
LSR-001,Laser Marking Station,Laser Marker,2500,Marking,No marking operation in this sample router
,Old Bridgeport Mill,Manual Mill,,Tool Room,Incomplete export row; unclear if active
```

## Expected ShopContext Notes

- Preserve machine names and asset IDs exactly.
- Preserve numeric work centers exactly.
- Do not invent operation-number mappings because this list does not contain operation numbers.
- Infer likely context from machine type, work center, and PRT instruction content only when supported.
- For `Op 0200 Machine First Side`, the PRT names CNC Mill `M-12`, but the machine list contains `Haas VF-2SS CNC Mill` and `Haas VF-4 CNC Mill` without saying which one is `M-12`; keep exact machine assignment uncertain.
- For `Op 0300 Machine Second Side`, keep CNC mill assignment uncertain for the same reason.
- Map `Manual Deburr Bench` and `Scotch-Brite Wheel` as likely context for `Op 0400 Deburr / Edge Break` when supported by work center and instruction content.
- Map `Chem Film Tank Line` as likely context for `Op 0500 Chem Film / Alodine`.
- Map `CMM Zeiss Contura` and `Height Gauge Station` as possible final inspection context, but do not assert CMM is always used.
- Keep `Laser Marking Station` visible as unmapped because no marking operation appears in the router.
- Mark `Old Bridgeport Mill` as incomplete/ambiguous with `Unknown` work center.
