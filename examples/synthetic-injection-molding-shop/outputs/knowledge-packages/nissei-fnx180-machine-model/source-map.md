# Source Map: Nissei FNX180 Machine Model

## Research Queries Used
- `Nissei FNX180 injection molding machine specifications official`
- `FNX180 Specifications NISSEI PLASTIC`

## Sources

| Source | Type | Tier | Location | Information Used | Confidence | Limitations |
|---|---|---:|---|---|---|---|
| Nissei FNX180 SME | generated SME shell | generated-input | `smes/nissei-fnx180-sme.md` | `IM-220` is approved backup press | high for mapping | Generated shell, not original backup qualification |
| shop-reference.md | generated shop context | generated-input | `shop-reference.md` | Backup-use condition for `PL-HOUSING-44` | high for mapping | No cycle/capacity/setup data |
| FNX180 Specifications | OEM public source | Tier 1 | https://www.nisseiplastic.com/en/products/fnx-4/spec.php?model=FNX180 | Public model specification context | high | Does not prove shop configuration, screw option, or process setup |

## Package Confidence
Input Mapping Confidence: high.

Technical Source Confidence: high for public model context; medium/low for shop execution impact.

Source Basis: generated SME shell plus OEM public source actually gathered.

## Missing Source Areas
- Shop backup qualification or validation record
- Current availability/schedule
- `MX-44A` setup sheet on `IM-220`
- Actual production rate comparison vs `IM-110`
