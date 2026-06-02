# Shop Reference

## 1. Shop Type / Process Context

This shop context covers an injection molding / plastics shop with two product flows:

- Thermoplastic Housing, part `PL-HOUSING-44`, route `RTR-PL-884`
- Elastomer Seal, part `EL-SEAL-12`, route `RTR-EL-201`

The shop performs material issue, material drying or preparation, mold setup, injection molding, compression molding, post cure, trim/gate removal, deflash, inspection, packaging, and conditional MRB disposition.

The router is the process skeleton. Machine and equipment assignments come from the uploaded machine list and user-confirmed mappings.

## 2. Standard Operation Flow

### Thermoplastic Housing - `PL-HOUSING-44` / `RTR-PL-884`

1. `010` - `Issue Resin` - work center `5100`
2. `020` - `Dry Material` - work center `5110`
3. `030` - `Setup Mold` - work center `5200`
4. `040` - `Mold Parts` - work center `5200`
5. `050` - `Trim/Gate` - work center `5300`
6. `060` - `Inspect` - work center `5400`
7. `070` - `Pack` - work center `5500`

Conditional operation excluded from standard flow:

- `095` - `MRB Hold` - work center `9999`; conditional MRB/disposition operation only.

### Elastomer Seal - `EL-SEAL-12` / `RTR-EL-201`

1. `010` - `Issue Material` - work center `5100`
2. `025` - `Prep Compound` - work center `Unknown`
3. `035` - `Compression Mold` - work center `5210`
4. `045` - `Post Cure` - work center `5120`
5. `055` - `Deflash` - work center `5300`
6. `065` - `Check` - work center `5400`
7. `075` - `Pack/Label` - work center `5500`

## 3. Operation Dictionary

| Product / Route | Operation # | Operation Name | Work Center | Plain-English Meaning | Notes |
|---|---:|---|---:|---|---|
| `PL-HOUSING-44` / `RTR-PL-884` | `010` | `Issue Resin` | `5100` | Issue resin from material storage | Source note: material from dry storage |
| `PL-HOUSING-44` / `RTR-PL-884` | `020` | `Dry Material` | `5110` | Dry thermoplastic resin before molding | Nylon and ABS/general resin use different dryers |
| `PL-HOUSING-44` / `RTR-PL-884` | `030` | `Setup Mold` | `5200` | Set up mold for molding operation | Mold `MX-44A` |
| `PL-HOUSING-44` / `RTR-PL-884` | `040` | `Mold Parts` | `5200` | Injection mold the housing parts | Press depends on scheduler |
| `PL-HOUSING-44` / `RTR-PL-884` | `050` | `Trim/Gate` | `5300` | Manually trim and remove gates | Uses trim bench |
| `PL-HOUSING-44` / `RTR-PL-884` | `060` | `Inspect` | `5400` | First article and hourly inspection checks | Uses optical/manual inspection equipment depending on characteristic |
| `PL-HOUSING-44` / `RTR-PL-884` | `070` | `Pack` | `5500` | Bag and box molded housings | Packaging operation |
| `PL-HOUSING-44` / `RTR-PL-884` | `095` | `MRB Hold` | `9999` | Conditional MRB/disposition hold | Not part of standard flow |
| `EL-SEAL-12` / `RTR-EL-201` | `010` | `Issue Material` | `5100` | Issue silicone material lot | Source note: silicone lot issued |
| `EL-SEAL-12` / `RTR-EL-201` | `025` | `Prep Compound` | `Unknown` | Manual/material-prep step | May be reduced or skipped if vendor-ready compound is supplied |
| `EL-SEAL-12` / `RTR-EL-201` | `035` | `Compression Mold` | `5210` | Compression mold elastomer seals | Uses compression molding press |
| `EL-SEAL-12` / `RTR-EL-201` | `045` | `Post Cure` | `5120` | Oven post cure for silicone/elastomer seals | Uses post cure oven |
| `EL-SEAL-12` / `RTR-EL-201` | `055` | `Deflash` | `5300` | Remove flash from molded elastomer seals | Current normal method is hand deflash |
| `EL-SEAL-12` / `RTR-EL-201` | `065` | `Check` | `5400` | Visual and dimensional inspection | Primarily manual inspection |
| `EL-SEAL-12` / `RTR-EL-201` | `075` | `Pack/Label` | `5500` | Package and label elastomer seals | Uses label printer for packaging labels |

## 4. Operation Step Summaries

### Thermoplastic Housing - `PL-HOUSING-44`

#### `010` - `Issue Resin`

- Material is issued from dry storage.
- No dedicated production machine is identified.

#### `020` - `Dry Material`

- Resin is dried before molding.
- `DRY-1` / Matsui Dryer 1 is used for nylon resin.
- `DRY-2` / Dri-Air Dryer 2 is used for ABS and general resin.
- `PL-HOUSING-44` can use either nylon or ABS depending on customer/material configuration, so both dryer mappings are valid material-dependent candidates.

#### `030` - `Setup Mold`

- Mold setup is performed for mold `MX-44A`.
- Setup occurs in work center `5200`, the injection molding work center.
- Setup supports the later `040 Mold Parts` operation.

#### `040` - `Mold Parts`

- Injection molding operation for `PL-HOUSING-44`.
- Normal candidate presses:
  - Primary: `IM-110` / Arburg Allrounder 470
  - Approved backup: `IM-220` / Nissei FNX180
- `IM-220` is used when `IM-110` is unavailable or scheduling requires it.

#### `050` - `Trim/Gate`

- Manual trim and gate removal operation.
- Uses `BENCH-TRIM` / Trim Bench.

#### `060` - `Inspect`

- First article and hourly checks are performed.
- Uses both `QC-1` / Vision Gauge 500 and `QC-2` / Granite Surface Plate depending on the inspection characteristic.
- This is a quality gate for the thermoplastic housing flow.

#### `070` - `Pack`

- Bag and box packaging operation.
- Packaging is performed in work center `5500`.

#### `095` - `MRB Hold`

- Conditional MRB/disposition operation.
- Excluded from the standard operation flow.

### Elastomer Seal - `EL-SEAL-12`

#### `010` - `Issue Material`

- Silicone lot is issued.
- No dedicated production machine is identified.

#### `025` - `Prep Compound`

- Manual/material-prep step.
- Normal owner is material preparation, not a dedicated machine.
- Work center remains `Unknown` unless later source data confirms a specific work center.
- If vendor-ready compound is supplied, this step may be reduced or skipped per the work order.

#### `035` - `Compression Mold`

- Compression molding operation for elastomer seals.
- Uses `CM-50` / Wabash Genesis Compression Press.

#### `045` - `Post Cure`

- Oven cure operation for silicone/elastomer seals.
- Uses `OV-9` / Blue M Post Cure Oven.

#### `055` - `Deflash`

- Current normal deflash method is hand deflash at `BENCH-TRIM` / Trim Bench.
- `CRYO-1` / Arrow Cryogenic Deflasher is down and should be treated only as a possible or alternate deflash method when available.

#### `065` - `Check`

- Visual and dimensional inspection operation.
- Primarily uses `QC-2` / Granite Surface Plate for manual inspection.
- `QC-1` / Vision Gauge 500 is used only when optical dimensional checks are required.
- This is a quality gate for the elastomer seal flow.

#### `075` - `Pack/Label`

- Packaging and customer label operation.
- Uses `LBL-1` / Zebra ZT411 Label Printer for packaging label print.

## 5. Work Center Dictionary

| Work Center | Inferred Meaning | Associated Operations / Equipment |
|---|---|---|
| `5100` | Material issue / material control | `Issue Resin`, `Issue Material` |
| `5110` | Resin drying | `Dry Material`; `DRY-1`, `DRY-2` |
| `5120` | Post cure oven area | `Post Cure`; `OV-9` |
| `5200` | Injection molding | `Setup Mold`, `Mold Parts`; `IM-110`, `IM-220` |
| `5210` | Compression molding | `Compression Mold`; `CM-50` |
| `5300` | Trim, gate removal, deflash | `Trim/Gate`, `Deflash`; `BENCH-TRIM`, alternate `CRYO-1` when available |
| `5400` | Inspection / dimensional checks | `Inspect`, `Check`; `QC-1`, `QC-2` |
| `5500` | Packaging / labeling | `Pack`, `Pack/Label`; `LBL-1` |
| `9999` | Conditional MRB/disposition | `MRB Hold` |
| `Unknown` | Unconfirmed work center | `Prep Compound` |

## 6. Machine / Equipment Dictionary

| Asset ID | Machine / Equipment Name | Type / Capability | Work Center | Associated Operation / Process | Notes |
|---|---|---|---|---|---|
| `IM-110` | Arburg Allrounder 470 | Injection Molding Press | `5200` | `PL-HOUSING-44` `040 Mold Parts` | Primary press for `PL-HOUSING-44`; source notes small housings and mold `MX-44A` sometimes |
| `IM-220` | Nissei FNX180 | Injection Molding Press | `5200` | `PL-HOUSING-44` `040 Mold Parts` | Approved backup press when `IM-110` is unavailable or scheduling requires it |
| `CM-50` | Wabash Genesis Compression Press | Compression Molding Press | `5210` | `EL-SEAL-12` `035 Compression Mold` | Elastomer seals |
| `DRY-1` | Matsui Dryer 1 | Resin Dryer | `5110` | `PL-HOUSING-44` `020 Dry Material` | Nylon drying |
| `DRY-2` | Dri-Air Dryer 2 | Resin Dryer | `5110` | `PL-HOUSING-44` `020 Dry Material` | ABS and general resin |
| `OV-9` | Blue M Post Cure Oven | Oven | `5120` | `EL-SEAL-12` `045 Post Cure` | Silicone post cure |
| `CRYO-1` | Arrow Cryogenic Deflasher | Deflash Machine | `5300` | Possible alternate for `EL-SEAL-12` `055 Deflash` | Status is down; not current normal method |
| `BENCH-TRIM` | Trim Bench | Manual Bench | `5300` | `PL-HOUSING-44` `050 Trim/Gate`; `EL-SEAL-12` `055 Deflash` | Hand trim, gate removal, and current normal hand deflash |
| `QC-1` | Vision Gauge 500 | Optical Inspection | `5400` | `PL-HOUSING-44` `060 Inspect`; conditional use for `EL-SEAL-12` `065 Check` | Dimensional checks; elastomer seal use only when optical dimensional checks are required |
| `QC-2` | Granite Surface Plate | Manual Inspection | `5400` | `PL-HOUSING-44` `060 Inspect`; `EL-SEAL-12` `065 Check` | Manual gauges; primary inspection equipment for elastomer seal checks |
| `LBL-1` | Zebra ZT411 Label Printer | Label Printer | `5500` | `EL-SEAL-12` `075 Pack/Label`; packaging label print | Packaging label print |
| `UNKNOWN-7` | Old Conair Dryer | Dryer | `Unknown` | No current mapped operation | Inactive; still on asset list; unknown if used |

## 7. Quality Gates

| Product / Route | Operation # | Operation Name | Gate Type | What Is Checked Or Decided | Equipment / Station |
|---|---:|---|---|---|---|
| `PL-HOUSING-44` / `RTR-PL-884` | `060` | `Inspect` | First article and hourly inspection | Inspection characteristics for molded housings | `QC-1` and `QC-2` depending on characteristic |
| `EL-SEAL-12` / `RTR-EL-201` | `065` | `Check` | Visual/dimensional inspection | Manual and dimensional checks for elastomer seals | Primarily `QC-2`; `QC-1` when optical dimensional checks are required |
| `PL-HOUSING-44` / `RTR-PL-884` | `095` | `MRB Hold` | Conditional MRB/disposition | Hold or disposition decision outside standard flow | Work center `9999` |

## 8. Shop-Specific Language

- `Issue Resin` and `Issue Material` are material issue operations, not molding operations.
- `Dry Material` is material-dependent for `PL-HOUSING-44`: nylon uses `DRY-1`, while ABS/general resin uses `DRY-2`.
- `Setup Mold` preserves mold `MX-44A` as an important shop-specific mold identifier.
- `Mold Parts` for `PL-HOUSING-44` can run on more than one approved press. `IM-110` is primary; `IM-220` is approved backup.
- `Prep Compound` for `EL-SEAL-12` is a manual/material-prep step with no confirmed work center. It may be reduced or skipped when vendor-ready compound is supplied.
- `Deflash` currently means hand deflash at `BENCH-TRIM`; `CRYO-1` is only an alternate possible method when available.
- `Inspect` and `Check` are quality gate terms. Equipment depends on product and inspection characteristic.
- `MRB Hold` is conditional MRB/disposition and is not part of standard production flow.
