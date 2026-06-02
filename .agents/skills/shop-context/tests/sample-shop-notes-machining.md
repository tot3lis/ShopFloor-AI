# Sample Shop Notes Machining

Synthetic user notes for ShopContext validation.

## Notes From Manufacturing Engineer

- `PRT` means process routing traveler.
- `Chem film` and `Alodine` are used interchangeably in older routers.
- `Final Insp` means `Final Inspection`.
- `Machine First Side` and `Machine 1st Side` mean the same operation.
- `2nd Op Machine` means second-side machining after the part is flipped.
- CNC work center `2200` has multiple mills; router usually does not specify the exact machine.
- `CMM` is used for final inspection when a dimensional report is required, but not every job requires CMM.
- Work center `2300` is deburr / edge break.
- Work center `2400` is chemical conversion coating.
- Work center `9000` is closeout / pack paperwork.

## Expected ShopContext Notes

- Use these notes to normalize alternate shop language without deleting original terms.
- Keep exact router names such as `Machine 1st Side`, `2nd Op Machine`, and `Final Insp`.
- Use uncertainty wording where the exact CNC mill or CMM use is not proven.
