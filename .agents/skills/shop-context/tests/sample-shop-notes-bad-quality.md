# Sample Shop Notes Bad Input Quality

Synthetic user/shop notes containing clarifications and contradictions.

## Notes From Manufacturing Engineer

- `VP` means vapor phase.
- `MY-200` and `MY200` are the same machine.
- `DEK Horizon 03` is the same as `DEK Horizon`.
- `Vapor Phase Oven` and `VAC 545` are the same asset.
- Work center `2120` is sometimes used in exports for vapor phase, but engineering usually calls VP work center `2110`.
- Wash is required for `CCA-CTRL-9001` after SMT even though one old router note says no wash.
- `CCA-CTRL-9002` has an SMT instruction, but it was not uploaded.
- `Old Washer Line` is retired and should not be treated as active.
- `Inspect` can mean AOI review or manual visual depending on the operation.
- Some routers repeat inspection operations when one is AOI and the other is manual visual.

## Expected ShopContext Notes

- Use these notes to resolve some aliases and retired-equipment status.
- Preserve remaining uncertainty when exact operation meaning or source conflict is unresolved.
- Preserve the router-vs-PRT conflict for `CCA-CTRL-9001` instead of pretending it never existed.
