# Source Map: Dimensional Inspection And Metrology

## Research Queries Used
- `NIST dimensional metrology calibration surface plate inspection`
- `ASME B89.3.7 granite surface plates standard flatness calibration`
- `VisionGauge 500 Series digital optical comparator specifications`
- `granite surface plate metrology height gage inspection purpose`

## Sources

| Source | Type | Tier | Location | Information Used | Confidence | Limitations |
|---|---|---:|---|---|---|---|
| Inspection SME | generated SME shell | generated-input | `smes/inspection-sme.md` | Shop inspection responsibilities and `QC-1`/`QC-2` use | high for mapping | Generated shell, no inspection plan |
| Granite Surface Plate SME | generated SME shell | generated-input | `smes/granite-surface-plate-sme.md` | `QC-2` manual/granite context | high for mapping | No calibration status |
| Vision Gauge 500 SME | generated SME shell | generated-input | `smes/vision-gauge-500-sme.md` | `QC-1` optical dimensional check context | high for mapping | No program/calibration data |
| ASME B89.3.7 Granite Surface Plates | standard publisher page | Tier 2 | https://www.asme.org/codes-standards/find-codes-standards/granite-surface-plates | Surface plate use, certification, recertification, uncertainty concepts | high for plate-standard context | Full standard not reproduced; public summary only |
| NIST Measurements and Calibrations | national metrology institute | Tier 2 | https://www.nist.gov/pml/productsservices/measurements-calibrations | Dimensional metrology and calibration context | medium/high | General NIST service page, not a shop procedure |
| VisionGauge 500 Series | OEM public source | Tier 1 | https://www.visionxinc.com/products/systems/digital-optical-comparators/500-series-digital-optical-comparators/ | Digital optical comparator capabilities and CAD comparison context | medium | Vendor page, not shop method approval |

## Package Confidence
Input Mapping Confidence: high.

Technical Source Confidence: medium.

Source Basis: generated SME shells plus public standards/NIST/OEM sources actually gathered.

## Missing Source Areas
- Shop inspection plan and controlling criteria
- Calibration certificates for `QC-1` and `QC-2`
- Gauge R&R or method validation
- Actual measurement results
