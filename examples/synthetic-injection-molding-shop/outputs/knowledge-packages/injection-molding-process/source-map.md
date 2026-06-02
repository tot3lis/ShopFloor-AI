# Source Map: Injection Molding Process

## Research Queries Used
- `injection molding process variables defects moisture sink warp flash technical guide`
- `ARBURG ALLROUNDER 470 H technical data injection molding machine official`
- `Nissei FNX180 injection molding machine specifications official`
- `resin drying nylon ABS injection molding moisture drying guide supplier`

## Sources

| Source | Type | Tier | Location | Information Used | Confidence | Limitations |
|---|---|---:|---|---|---|---|
| Generated SME shells | generated shop context | generated-input | `smes/*.md` | Shop press roles, operations, work centers, material-dependent dryer relationship | high for mapping | Generated shell, not an original router or work instruction |
| shop-reference.md | generated shop context | generated-input | `shop-reference.md` | `IM-110` primary, `IM-220` backup, `MX-44A`, nylon/ABS routing context | high for mapping | Does not include process recipe, cycle time, or capacity |
| ARBURG ALLROUNDER 470 H technical data | OEM public source | Tier 1 | https://www.arburg.com/media/daten/publications/technical_data/hybrid_machines/ARBURG_ALLROUNDER_470H_TD_680315_en_US.pdf | Close model-family press context | medium | Asset is named Allrounder 470, exact variant not confirmed |
| Nissei FNX180 specifications | OEM public source | Tier 1 | https://www.nisseiplastic.com/en/products/fnx-4/spec.php?model=FNX180 | Public FNX180 model context | high | Does not prove shop configuration or setup |
| Injection molding defect/process guidance | general process source | Tier 4/5 | https://en.wikipedia.org/wiki/Injection_moulding | Generic defect mechanisms and process phases | low/medium | Broad reference; not controlling source |
| Novatec resin drying basics | technical vendor source | Tier 3 | https://www.novatec.com/knowledge-center/resin-moisture-drying/resin-drying-basics/ | Moisture-control principles that interact with molding | medium | General dryer/process guidance, not material-specific shop recipe |

## Package Confidence
Input Mapping Confidence: high.

Technical Source Confidence: medium.

Source Basis: generated SME shells plus public OEM/model and process sources actually gathered.

## Missing Source Areas
- Shop-approved setup sheets
- `MX-44A` mold drawings or maintenance history
- Press cycle-time/capacity records
- Material supplier data sheets for the exact resin grades
- Actual defect, inspection, or production records
