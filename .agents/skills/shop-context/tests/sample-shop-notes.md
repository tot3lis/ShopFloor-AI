# Sample Shop Notes

Synthetic user notes for ShopContext validation.

## Notes From Manufacturing Engineer

- `VP` means vapor phase.
- `Sec side` means secondary side.
- `Pri side` means primary side.
- `PNP` means pick-and-place.
- `Process Secondary Side` usually includes paste, PNP, VP, wash, and bake for this product family.
- `Primary Side Process` and `Process Primary Side` are usually the same kind of router operation, but the primary-side instruction is not included in this sample package.
- `Inspection` may mean AOI or manual visual depending on the operation.
- `E-Test`, `Electrical Test`, and `Functional Test` may refer to the same final electrical test area, but confirm if the route uses a special test fixture.
- Work center `2110` is the SMT process area, but keep the raw work center code in the reference.
- Work center `2210` is inspection/AOI review.
- Work center `4100` is final QA.

## Expected ShopContext Notes

- Use these notes to normalize shop language without deleting the original shop terms.
- Put alternate names and overloaded terms in `Shop-Specific Language`.
- Use the notes to support likely interpretation, but still preserve uncertainty where the note says to confirm.
