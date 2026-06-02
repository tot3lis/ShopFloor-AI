# Knowledge Package Registry

## Purpose
This registry lists reusable Layer 4 technical knowledge packages derived from generated manufacturing SME inputs.

## Source Inputs

| Input | Present | Notes |
|---|---:|---|
| sme-registry.md | yes | 15 generated SMEs reviewed |
| smes/*.md | 15 | Generated SME shells reviewed |
| shop-reference.md | yes | Used for shop-specific mapping only |
| user-uploaded documents | no | No shop manuals, work instructions, inspection criteria, or actual records were uploaded |
| public sources | yes | Targeted public/OEM/vendor/standards-style sources were gathered for sourceable package candidates |

## Packages

| Package | Type | Scope | Derived From SME(s) | Input Mapping Confidence | Technical Source Confidence | Source Tier Coverage | Source Basis | Limitations |
|---|---|---|---|---|---|---|---|---|
| `manufacturing-operation-flow` | domain-general | Operation sequence, work center handoffs, standard vs conditional route status | Shop Flow SME; Inspection SME | high | low | generated-input; general reasoning | generated SME shell + sme-registry.md + shop-reference.md | No router control procedure, travelers, schedule, capacity model, or execution records. |
| `injection-molding-process` | process-family | Injection molding process principles, variables, and failure mechanisms for thermoplastic housings | Arburg Allrounder 470 SME; Nissei FNX180 SME; MX-44A Mold SME | high | medium | Tier 1 OEM model context; Tier 3-5 process/supplier/trade sources | generated SME shell + public sources | Not shop-approved settings; no press setup sheets or `MX-44A` tooling data. |
| `arburg-allrounder-470h-machine-model` | machine-model | Public model context for ARBURG ALLROUNDER 470 H / Allrounder 470 family press | Arburg Allrounder 470 SME | medium | medium | Tier 1 OEM technical data | generated SME shell + public OEM source | Shop asset is named Arburg Allrounder 470, while public source is 470 H; use as close model-family context unless exact asset variant is confirmed. |
| `nissei-fnx180-machine-model` | machine-model | Public model context for Nissei FNX180 injection molding machine | Nissei FNX180 SME | high | high | Tier 1 OEM specifications | generated SME shell + public OEM source | Does not prove shop configuration, screw option, setup, or cycle capability. |
| `compression-molding-process` | process-family | Compression molding principles, variables, and elastomer seal failure mechanisms | Wabash Genesis Compression Press SME | high | medium | Tier 1 OEM equipment-family source; Tier 3-5 process sources | generated SME shell + public sources | No shop process spec, material compound spec, mold data, or cure criteria. |
| `wabash-genesis-compression-press-family` | equipment-family | Wabash Genesis press family capability context | Wabash Genesis Compression Press SME | high | high | Tier 1 OEM source | generated SME shell + public OEM source | Family-level context only; does not prove exact shop press configuration or platen options. |
| `resin-drying-material-conditioning` | process-subtype | Resin drying and moisture-control principles for nylon and ABS/general resin | Matsui Dryer 1 SME; Dri-Air Dryer 2 SME; Old Conair Dryer SME | high | medium | Tier 3 supplier/processor sources; Tier 5 trade/process sources | generated SME shell + public sources | No shop drying recipe, actual dryer records, or material-specific customer requirements. |
| `mold-tooling-setup` | equipment-family | Mold/tooling setup context for `MX-44A` and housing molding | MX-44A Mold SME; Arburg Allrounder 470 SME; Nissei FNX180 SME | high | low | generated-input; general injection molding source context | generated SME shell + public process sources | No mold drawing, setup sheet, maintenance history, or press-specific setup record. |
| `post-cure-oven-processing` | process-subtype | Oven post-cure principles for silicone/elastomer parts | Blue M Post Cure Oven SME | high | low | Tier 3 supplier-style source; generated-input | generated SME shell + public source | No material cure spec, oven manual, temperature uniformity data, or shop cure record. |
| `trim-and-deflash` | process-subtype | Manual trim, hand deflash, and alternate cryogenic deflash principles | Trim Bench SME; Arrow Cryogenic Deflasher SME | high | medium | Tier 3-5 vendor/process sources | generated SME shell + public sources | No shop visual standard, deflash criteria, or `CRYO-1` qualification/status record. |
| `dimensional-inspection-and-metrology` | inspection-or-test-method | Manual/optical dimensional inspection principles and method selection | Inspection SME; Granite Surface Plate SME; Vision Gauge 500 SME | high | medium | Tier 2 standards/NIST-style sources; Tier 1 OEM optical comparator source; Tier 3 vendor bulletin | generated SME shell + public sources | No shop inspection plan, tolerance criteria, calibration certificates, or measurement results. |
| `granite-surface-plate-metrology` | inspection-or-test-method | Granite surface plate use, calibration, uncertainty, and manual-gauging context | Granite Surface Plate SME; Inspection SME | high | high | Tier 2 ASME/NIST-style sources; Tier 3 Mitutoyo bulletin | generated SME shell + public sources | Does not prove the shop plate grade, calibration status, or gauge setup. |
| `visiongauge-500-optical-comparator` | machine-model | Public model context for VisionGauge 500 Series digital optical comparator | Vision Gauge 500 SME | high | medium | Tier 1 OEM source | generated SME shell + public OEM source | Does not prove shop configuration, program, calibration, or approved inspection method. |
| `packaging-and-labeling` | process-subtype | Thermal/direct thermal/thermal-transfer label printing variables and quality mechanisms | Zebra ZT411 Label Printer SME; Shop Flow SME | high | medium | Tier 1 OEM and OEM guide sources | generated SME shell + public sources | No customer label requirements, label templates, or print verification records. |
| `zebra-zt411-printer-model` | machine-model | Public model context for Zebra ZT411 industrial printer | Zebra ZT411 Label Printer SME | high | high | Tier 1 OEM product/spec sources | generated SME shell + public OEM source | Does not prove shop media, ribbon, printhead condition, template, or label approval. |

## Deferred Opportunities

| Candidate Package | Reason Deferred | Needed Source Or Input |
|---|---|---|
| `mx-44a-tooling-package` | Mold is named, but no source covers the exact mold. | Mold drawing, setup sheet, press fit/setup requirements, maintenance records. |
| `matsui-dryer-1-machine-model` | Dryer is named, but no credible exact model source was gathered. | Matsui Dryer 1 manual/specification, shop drying recipe. |
| `dri-air-dryer-2-machine-model` | Dryer is named, but no credible exact model source was gathered. | Dri-Air Dryer 2 manual/specification, shop drying recipe. |
| `blue-m-post-cure-oven-model` | Oven is named, but no exact model/manual source was gathered. | Blue M oven model/manual, cure profile, temperature uniformity data. |
| `arrow-cryogenic-deflasher-model` | Deflasher is named, but no exact Arrow model source was gathered. | Arrow model manual, status/qualification records, deflash criteria. |
| `inspection-plan-and-acceptance-criteria` | Acceptance method cannot be generated from public sources. | Shop inspection plan, customer criteria, gauge instructions, calibration records. |
