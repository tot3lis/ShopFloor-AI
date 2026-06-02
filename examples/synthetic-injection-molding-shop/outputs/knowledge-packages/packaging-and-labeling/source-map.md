# Source Map: Packaging And Labeling

## Research Queries Used
- `Zebra ZT411 industrial printer specifications official`
- `thermal transfer label printing print quality variables ribbon media heat speed pressure guide Zebra`

## Sources

| Source | Type | Tier | Location | Information Used | Confidence | Limitations |
|---|---|---:|---|---|---|---|
| Zebra ZT411 Label Printer SME | generated SME shell | generated-input | `smes/zebra-zt411-label-printer-sme.md` | Shop `PKG-1` operation mapping | high for mapping | No template/customer requirements |
| Zebra ZT411 product page | OEM public source | Tier 1 | https://www.zebra.com/us/en/products/printers/industrial/zt400-series/zt411.html | ZT411 public capabilities and use cases | high for model context | Does not prove shop config |
| Zebra direct thermal vs thermal transfer FAQ | OEM public source | Tier 1 | https://www.zebra.com/us/en/resource-library/faq/difference-between-direct-thermal-and-thermal-transfer-printing.html | Printing technology difference and media/ribbon compatibility | medium/high | General guidance |
| Zebra ZT400 setup support | OEM support source | Tier 1 | https://supportcommunity.zebra.com/articles/en_US/Knowledge/ZT400-Series-Initial-Printer-Setup-Details-and-Information | Setup variables such as pressure/print quality context | medium | Support article, not shop procedure |

## Package Confidence
Input Mapping Confidence: high.

Technical Source Confidence: medium.

Source Basis: generated SME shell plus OEM public/support sources actually gathered.

## Missing Source Areas
- Label templates and customer requirements
- Media/ribbon specification
- Barcode verification criteria
