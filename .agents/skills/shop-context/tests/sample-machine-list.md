# Sample Machine List

Synthetic CSV-style machine export for ShopContext V1 validation. This is not executable test data.

## Machine Export

```csv
machine_name,machine_type,work_center,user_note
DEK Horizon,Stencil Printer,1100,used for solder paste print
MY200,Pick and Place,1100,main SMT placement machine
Shared SMT Line,SMT Line,1100,used for both screen print support and component placement support
Koh Young Zenith,AOI,1200,AOI inspection system
VAC 545,Vapor Phase,1300,reflow soldering
Hioki Tester,Electrical Test,1500,functional/electrical test
Manual Inspection Bench,Inspection,,used for final visual inspection
Conformal Coat Booth,Coating,1700,no matching operation in basic router
Bench A,Inspection,1400,manual inspection area
Bench B,Inspection,1400,backup inspection area
Legacy Reflow Oven,Reflow,9999,listed in asset export but not normally used
```

## Expected ShopContext Notes

- Preserve machine names exactly.
- Preserve machine types exactly.
- Preserve numeric work centers exactly.
- Empty work center should be `Unknown`.
- Do not assume one work center equals one machine.
- Allow multiple machines in the same work center.
- Allow one machine to support multiple operations when source notes support it.
- Do not force one-to-one operation-to-machine mapping.
- Shared SMT Line should be allowed to support both screen print support and component placement support if the source note supports it.
- Still preserve uncertainty if the exact operation-machine relationship is unclear.
- Bench A and Bench B should create ambiguity for manual/final inspection mapping.
- Legacy Reflow Oven has a conflicting or unmatched work center and should be flagged.
- Conformal Coat Booth should remain visible as unmapped if no router operation matches it.
- Evidence sources should be labeled `Possible` unless the source explicitly confirms retention.
