# Sample Router Multiple Products

Synthetic CSV-style router export for testing multiple product flows with overlapping operations, numeric work centers, inconsistent naming, and route-role differences.

## Router Export

```csv
part_number,operation_number,operation_name,work_center,user_note
CCA-A,010,Kit Material,1000,material issue
CCA-A,020,Screen Print,1100,paste print
CCA-A,030,Place Components,1100,SMT placement
CCA-A,040,Inspect,1200,AOI
CCA-A,050,Reflow,1300,vapor phase
CCA-A,060,Final Inspect,1400,manual inspection
CCA-A,070,Electrical Test,1500,functional test
CCA-A,095,MRB Disposition,9000,only if nonconformance requires review
CCA-B,010,Kit Material,1000,material issue
CCA-B,025,Stencil Print,1100,paste print same area as CCA-A op 020
CCA-B,035,Pick Place,1100,SMT placement same area as CCA-A op 030
CCA-B,045,AOI Review,1200,inspection after placement
CCA-B,050,Reflow,1300,vapor phase
CCA-B,065,Rework Repair,1600,conditional rework only
CCA-B,080,Test,1500,functional test
```

## Expected ShopContext Notes

- Preserve product-specific flows.
- Do not flatten CCA-A and CCA-B into one fake universal route.
- Mark CCA-A Op 020 `Screen Print` and CCA-B Op 025 `Stencil Print` as possible equivalents, not proven equivalents.
- Mark CCA-A Op 030 `Place Components` and CCA-B Op 035 `Pick Place` as possible equivalents, not proven equivalents.
- Preserve CCA-A Op 095 `MRB Disposition` separately from standard flow unless the source says it is standard.
- Preserve CCA-B Op 065 `Rework Repair` separately from standard flow unless the source says it is standard.
- Preserve numeric work centers exactly.
- Label inferred work center meanings as inferred.
- Treat user notes as context only, not proof of actual execution.

