# Source Map: Manufacturing Operation Flow

## Research Queries Used
- No public research required; package scope is shop routing context from generated Layer 1-2 outputs.

## Sources

| Source | Type | Tier | Location | Information Used | Confidence | Limitations |
|---|---|---:|---|---|---|---|
| shop-reference.md | generated shop context | generated-input | `shop-reference.md` | Standard and conditional operation flow, primary/backup resources | high for mapping | Generated from uploaded inputs; not execution evidence |
| sme-registry.md | generated registry | generated-input | `sme-registry.md` | SME ownership and routing | high for mapping | No live schedule/capacity |
| Generated SME shells | generated SME context | generated-input | `smes/*.md` | Flow-relevant SME roles | high for mapping | Generated shells, not work instructions |

## Package Confidence
Input Mapping Confidence: high.

Technical Source Confidence: low.

Source Basis: generated SME shells and shop-reference.md only.

## Missing Source Areas
- Live schedule and WIP status
- Capacity/cycle-time records
- Router control procedure
- Actual traveler or batch records
