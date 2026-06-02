# Sample Router Basic

Synthetic CSV-style router export for ShopContext V1 validation. This is not executable test data.

## Router Export

```csv
operation_number,operation_name,work_center,user_note
010,Kit Material,1000,material issue before build
020,Screen Print,1100,solder paste print
030,Place Components,1100,SMT placement
040,Inspect,1200,AOI after placement
050,Reflow,1300,vapor phase solder
060,Final Inspect,1400,manual final inspection
070,Electrical Test,1500,functional test
```

## Expected ShopContext Notes

- Preserve operation numbers exactly.
- Preserve operation names exactly.
- Preserve numeric work centers exactly.
- Do not rename work center `1100` as SMT unless clearly labeled as inferred.
- Use `user_note` only as context, not proof of actual execution.
- Infer likely plain-English meaning from `operation_name` and `user_note` where reasonable.
- Treat router as planned flow, not evidence that a specific unit completed the route.
- Identify inspection/test points from operation names and user notes.
- Identify likely manual operations when supported by names and notes.
- Do not over-interpret generic operation names such as `Inspect`.

