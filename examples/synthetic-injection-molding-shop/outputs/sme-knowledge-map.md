# SME Knowledge Map

## Purpose
This map connects generated SME shells to reusable Layer 4 knowledge packages. It does not modify SME scope, shop authority, or approval status.

## Source Inputs

| Input | Present | Notes |
|---|---:|---|
| sme-registry.md | yes | 15 generated SMEs reviewed |
| smes/*.md | 15 | All generated SME shells reviewed |
| shop-reference.md | yes | Used as supporting shop context |
| user-uploaded documents | no | No shop manuals, specs, procedures, criteria, or records supplied |
| public sources | yes | Targeted public-source search performed for sourceable packages |

## SME: Shop Flow SME

Role: Shop flow

Owned scope: Standard and conditional operation flow across `PL-HOUSING-44` and `EL-SEAL-12`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| manufacturing-operation-flow | domain-general | The SME owns route sequence, work centers, and standard-vs-conditional operation context. | high | low | Supports flow reasoning only; cannot prove actual execution or capacity. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| injection-molding-process | process-family | Helps interpret `PL-HOUSING-44` molding flow. | medium | medium | Does not make Shop Flow SME a press/process authority. |
| compression-molding-process | process-family | Helps interpret `EL-SEAL-12` molding flow. | medium | medium | Does not expand ownership into process settings. |
| dimensional-inspection-and-metrology | inspection-or-test-method | Helps route quality-gate questions to inspection SMEs. | medium | medium | Inspection decisions remain with inspection/quality context. |

### Missing Package Opportunities

- `router-control-procedure`: would improve flow authority if uploaded.

### Boundaries And Cautions

- Cannot prove a specific unit followed the route without records.
- Cannot define approved recipes, cycle times, capacity, or acceptance criteria.

## SME: Inspection SME

Role: Inspection coordinator

Owned scope: Quality gates at `060 Inspect`, `065 Check`, and conditional `095 MRB Hold`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| dimensional-inspection-and-metrology | inspection-or-test-method | The SME coordinates manual and optical inspection methods. | high | medium | Does not prove shop criteria, calibration, or pass/fail status. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| granite-surface-plate-metrology | inspection-or-test-method | Supports surface-plate-specific manual inspection reasoning. | high | high | Does not make Inspection SME owner of gauge setup. |
| visiongauge-500-optical-comparator | machine-model | Supports optical comparator context when `QC-1` is involved. | medium | medium | Does not prove shop program/calibration. |
| manufacturing-operation-flow | domain-general | Helps locate inspection gates in the route. | high | low | Does not expand inspection authority into production routing. |

### Missing Package Opportunities

- `inspection-plan-and-acceptance-criteria`: needs uploaded inspection plans, criteria, and gauge instructions.

### Boundaries And Cautions

- Cannot accept/reject parts without controlling criteria and actual results.

## SME: Arburg Allrounder 470 SME

Role: Machine / Capability

Owned scope: `IM-110` primary injection molding press for `PL-HOUSING-44` `040 Mold Parts`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| injection-molding-process | process-family | `IM-110` is an injection molding press tied to standard molding. | high | medium | General process package; not shop-approved settings. |
| arburg-allrounder-470h-machine-model | machine-model | Public ARBURG 470 H/Allrounder 470 family data provides close model-family context. | medium | medium | Treat as close model-family context until exact asset variant is confirmed. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| mold-tooling-setup | equipment-family | `MX-44A` tooling appears in setup/molding context. | high | low | Does not make this SME the tooling authority. |
| resin-drying-material-conditioning | process-subtype | Upstream drying affects molded housing context. | medium | medium | Does not expand ownership into material drying. |
| dimensional-inspection-and-metrology | inspection-or-test-method | Downstream inspection checks molded housings. | medium | medium | Does not expand ownership into inspection decisions. |

### Missing Package Opportunities

- `arburg-allrounder-470-exact-asset`: needs exact machine variant/manual and shop setup data.

### Boundaries And Cautions

- Cannot claim actual press settings, run history, machine condition, or defect causation.

## SME: Nissei FNX180 SME

Role: Machine / Capability

Owned scope: `IM-220` approved backup injection molding press for `PL-HOUSING-44` `040 Mold Parts`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| injection-molding-process | process-family | `IM-220` is an injection molding press tied to the standard molding operation as approved backup. | high | medium | General process package; not shop-approved settings. |
| nissei-fnx180-machine-model | machine-model | Public Nissei FNX180 specifications provide model context. | high | high | Does not prove shop screw option, setup, equivalency, or actual usage. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| mold-tooling-setup | equipment-family | Backup press context interacts with the `MX-44A` mold setup. | medium | low | Does not establish press-tooling equivalency limits. |
| manufacturing-operation-flow | domain-general | Helps explain backup use when `IM-110` is unavailable or scheduling requires it. | high | low | Does not quantify capacity impact. |

### Missing Package Opportunities

- `nissei-fnx180-shop-backup-qualification`: needs approved backup setup records and process comparison data.

### Boundaries And Cautions

- Cannot prove backup setup equivalence, cycle-time impact, or actual usage.

## SME: Wabash Genesis Compression Press SME

Role: Machine / Capability

Owned scope: `CM-50` compression molding for `EL-SEAL-12` `035 Compression Mold`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| compression-molding-process | process-family | `CM-50` is a compression molding press for elastomer seals. | high | medium | General process package; not shop-approved settings. |
| wabash-genesis-compression-press-family | equipment-family | Wabash Genesis public source supports family-level capability context. | high | high | Does not prove exact shop configuration or platen options. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| post-cure-oven-processing | process-subtype | Post cure follows compression molding for seals. | medium | low | Does not expand ownership into cure recipes. |
| trim-and-deflash | process-subtype | Deflash follows molding/post cure in the seal flow. | medium | medium | Does not expand ownership into deflash methods. |

### Missing Package Opportunities

- `elastomer-seal-compression-mold-spec`: needs material, mold, and process documentation.

### Boundaries And Cautions

- Cannot define molding force, time, temperature, or actual molding evidence.

## SME: Matsui Dryer 1 SME

Role: Machine / Capability

Owned scope: `DRY-1` nylon drying for `PL-HOUSING-44` `020 Dry Material`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| resin-drying-material-conditioning | process-subtype | `DRY-1` is the nylon dryer for material-dependent housing flow. | high | medium | Does not define shop drying recipe or actual material condition. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| injection-molding-process | process-family | Dried resin feeds the injection molding operation. | medium | medium | Dryer SME does not own molding press parameters. |

### Missing Package Opportunities

- `matsui-dryer-1-machine-model`: needs exact dryer manual/specification.

### Boundaries And Cautions

- Cannot claim drying time, temperature, dew point, or moisture acceptability.

## SME: Dri-Air Dryer 2 SME

Role: Machine / Capability

Owned scope: `DRY-2` ABS/general resin drying for `PL-HOUSING-44` `020 Dry Material`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| resin-drying-material-conditioning | process-subtype | `DRY-2` is the ABS/general resin dryer for material-dependent housing flow. | high | medium | Does not define shop drying recipe or actual material condition. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| injection-molding-process | process-family | Dried resin feeds the injection molding operation. | medium | medium | Dryer SME does not own molding press parameters. |

### Missing Package Opportunities

- `dri-air-dryer-2-machine-model`: needs exact dryer manual/specification.

### Boundaries And Cautions

- Cannot claim drying time, temperature, dew point, or moisture acceptability.

## SME: Blue M Post Cure Oven SME

Role: Machine / Capability

Owned scope: `OV-9` post cure oven for `EL-SEAL-12` `045 Post Cure`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| post-cure-oven-processing | process-subtype | `OV-9` is tied to silicone/elastomer post cure. | high | low | Does not define cure profile or shop-approved recipe. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| compression-molding-process | process-family | Post cure follows compression molding for seals. | medium | medium | Oven SME does not own molding operation. |
| trim-and-deflash | process-subtype | Deflash follows cure in the seal flow. | medium | medium | Oven SME does not own deflash criteria. |

### Missing Package Opportunities

- `blue-m-post-cure-oven-model`: needs exact oven manual and cure profile.

### Boundaries And Cautions

- Cannot claim actual cure status without oven records or acceptance criteria.

## SME: Arrow Cryogenic Deflasher SME

Role: Machine / Capability

Owned scope: `CRYO-1` alternate cryogenic deflash for `EL-SEAL-12` `055 Deflash`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| trim-and-deflash | process-subtype | `CRYO-1` is an alternate deflash method when available. | high | medium | Does not prove current availability or approved parameters. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| dimensional-inspection-and-metrology | inspection-or-test-method | Deflash quality may be checked by inspection. | medium | medium | Deflasher SME does not own inspection acceptance. |

### Missing Package Opportunities

- `arrow-cryogenic-deflasher-model`: needs exact model manual and status/qualification records.

### Boundaries And Cautions

- `CRYO-1` is down in current context and is not current normal method.

## SME: Trim Bench SME

Role: Machine / Capability

Owned scope: `BENCH-TRIM` manual trim, gate removal, and current hand deflash.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| trim-and-deflash | process-subtype | `BENCH-TRIM` owns current manual trim/gate and hand deflash work. | high | medium | Does not define shop workmanship or visual acceptance criteria. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| dimensional-inspection-and-metrology | inspection-or-test-method | Inspection may evaluate trim/deflash outcomes. | medium | medium | Trim Bench SME does not own accept/reject decision. |

### Missing Package Opportunities

- `trim-deflash-workmanship-standard`: needs visual standards and work instructions.

### Boundaries And Cautions

- Cannot determine acceptable flash/gate condition without criteria.

## SME: Vision Gauge 500 SME

Role: Machine / Capability

Owned scope: `QC-1` optical inspection for `060 Inspect` and conditional `065 Check`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| dimensional-inspection-and-metrology | inspection-or-test-method | `QC-1` is optical dimensional inspection equipment. | high | medium | Does not define shop measurement programs, tolerances, or calibration status. |
| visiongauge-500-optical-comparator | machine-model | Public VisionGauge 500 Series source supports model-family optical comparator context. | high | medium | Does not prove shop configuration, program, calibration, or approved inspection method. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| manufacturing-operation-flow | domain-general | Helps place inspection in product flow. | medium | low | Does not expand gauge SME into route ownership. |

### Missing Package Opportunities

- `visiongauge-500-shop-programs`: needs gauge program documentation and calibration records.

### Boundaries And Cautions

- Cannot decide pass/fail without acceptance criteria and actual measurements.

## SME: Granite Surface Plate SME

Role: Machine / Capability

Owned scope: `QC-2` manual dimensional inspection using Granite Surface Plate.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| granite-surface-plate-metrology | inspection-or-test-method | `QC-2` is manual dimensional inspection equipment using a surface plate. | high | high | Does not define the shop plate grade, calibration status, or gauge setup. |
| dimensional-inspection-and-metrology | inspection-or-test-method | Surface plate use is part of broader dimensional metrology. | high | medium | Does not define tolerances or acceptance criteria. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| manufacturing-operation-flow | domain-general | Helps place inspection in product flow. | medium | low | Does not expand gauge SME into route ownership. |

### Missing Package Opportunities

- `manual-gauge-inspection-procedure`: needs gauge instructions, inspection plan, and calibration records.

### Boundaries And Cautions

- Cannot decide pass/fail without acceptance criteria and actual measurements.

## SME: Zebra ZT411 Label Printer SME

Role: Machine / Capability

Owned scope: `LBL-1` label printing for `EL-SEAL-12` `075 Pack/Label`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| packaging-and-labeling | process-subtype | `LBL-1` supports packaging label print. | high | medium | Does not define shop label content, template, or customer requirement. |
| zebra-zt411-printer-model | machine-model | Zebra public sources support ZT411 model context. | high | high | Does not prove shop media, ribbon, printhead state, or approved template. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| manufacturing-operation-flow | domain-general | Helps place label printing in final route sequence. | medium | low | Does not expand label SME into packaging ownership beyond its scope. |

### Missing Package Opportunities

- `zebra-zt411-shop-label-templates`: needs label templates, customer requirements, and print verification records.

### Boundaries And Cautions

- Cannot validate label content without customer/packaging requirements.

## SME: Old Conair Dryer SME

Role: Machine / Capability

Owned scope: `UNKNOWN-7` inactive Old Conair Dryer with no current mapped operation.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| resin-drying-material-conditioning | process-subtype | The item is a dryer, but inactive and unmapped. | low | medium | Context only; not current standard route support. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| manufacturing-operation-flow | domain-general | Helps avoid routing normal drying questions to this inactive dryer. | low | low | Does not make this asset route-supported. |

### Missing Package Opportunities

- `old-conair-dryer-status`: needs asset disposition/status records.

### Boundaries And Cautions

- Current relevance is unknown; do not route normal drying questions here unless the user names this asset.

## SME: MX-44A Mold SME

Role: Machine / Capability

Owned scope: `MX-44A` mold/tooling for `030 Setup Mold` and `040 Mold Parts`.

### Primary Packages

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| mold-tooling-setup | equipment-family | `MX-44A` is named tooling in the housing setup and molding flow. | high | low | Does not define mold design, condition, or setup parameters. |

### Context Packages

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| injection-molding-process | process-family | The mold is used in injection molding context. | high | medium | Tooling SME does not own press operation. |
| arburg-allrounder-470h-machine-model | machine-model | Primary press model-family context may matter to mold setup questions. | medium | medium | Does not prove shop press/mold compatibility. |
| nissei-fnx180-machine-model | machine-model | Backup press model context may matter to mold setup questions. | medium | high | Does not prove shop press/mold compatibility. |
| dimensional-inspection-and-metrology | inspection-or-test-method | Molded part dimensions are checked downstream. | medium | medium | Tooling SME does not own inspection acceptance. |

### Missing Package Opportunities

- `mx-44a-tooling-package`: needs mold drawing, setup sheet, tooling maintenance records, and press-specific setup documentation.

### Boundaries And Cautions

- Cannot infer mold condition, cavity state, or dimensional effect without tooling evidence.
