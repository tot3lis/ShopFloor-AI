# SME Coverage Map

## 1. Source Reviewed

- `shop-reference.md`

## 2. Generated SME Types

| SME Type | Generated | Notes |
|---|---:|---|
| Shop Flow SME | yes | Always generated from standard operation flow and work center relationships |
| Inspection SME | yes | Always generated from quality gates and inspection equipment |
| Machine / Capability SMEs | yes | Generated for named machines, equipment, fixtures, benches, and assets in `shop-reference.md` |
| User-requested SMEs | no | No additional user-requested SMEs were provided |

## 3. Shop Flow Summary

The shop reference describes an injection molding / plastics shop with two product flows: `PL-HOUSING-44` thermoplastic housing and `EL-SEAL-12` elastomer seal. The flow includes material issue, drying or compound prep, mold setup, molding, trim/deflash, inspection, packaging, and conditional MRB disposition.

## 4. Required SMEs

| SME | SME Type | Why Needed | Supporting ShopContext Evidence | Source Depth | Confidence |
|---|---|---|---|---|---|
| Shop Flow SME | Shop flow | Required global flow coordinator | Standard operation flow for `PL-HOUSING-44` and `EL-SEAL-12` | Level 3 | High |
| Inspection SME | Inspection coordinator | Required inspection coordinator | Quality gates at `060 Inspect`, `065 Check`, and conditional `095 MRB Hold` | Level 3 | High |
| Arburg Allrounder 470 SME | Machine / Capability | Primary injection molding press for `PL-HOUSING-44` | `IM-110` tied to standard `040 Mold Parts` | Level 3 | High |
| Nissei FNX180 SME | Machine / Capability | Approved backup injection molding press tied to standard route | `IM-220` tied to standard `040 Mold Parts` as approved backup | Level 3 | Medium |
| Wabash Genesis Compression Press SME | Machine / Capability | Compression molding press for elastomer seals | `CM-50` tied to standard `035 Compression Mold` | Level 3 | High |
| Matsui Dryer 1 SME | Machine / Capability | Dryer for nylon material configuration | `DRY-1` tied to standard `020 Dry Material` | Level 3 | High |
| Dri-Air Dryer 2 SME | Machine / Capability | Dryer for ABS/general resin material configuration | `DRY-2` tied to standard `020 Dry Material` | Level 3 | High |
| Blue M Post Cure Oven SME | Machine / Capability | Oven for elastomer seal post cure | `OV-9` tied to standard `045 Post Cure` | Level 3 | High |
| Trim Bench SME | Machine / Capability | Manual bench for standard trim and deflash work | `BENCH-TRIM` tied to `050 Trim/Gate` and `055 Deflash` | Level 3 | High |
| Vision Gauge 500 SME | Machine / Capability | Optical inspection equipment for standard inspection gates | `QC-1` tied to `060 Inspect` and conditional use for `065 Check` | Level 3 | High |
| Granite Surface Plate SME | Machine / Capability | Manual inspection equipment for standard inspection gates | `QC-2` tied to `060 Inspect` and primary `065 Check` | Level 3 | High |
| Zebra ZT411 Label Printer SME | Machine / Capability | Label printer tied to standard pack/label operation | `LBL-1` tied to `075 Pack/Label` | Level 3 | High |
| MX-44A Mold SME | Machine / Capability | Named mold used in thermoplastic housing setup | `MX-44A` tied to `030 Setup Mold` and `040 Mold Parts` context | Level 3 | High |

## 5. Conditional SMEs

| SME | SME Type | Why Conditional | Supporting ShopContext Evidence | Source Depth | Confidence |
|---|---|---|---|---|---|
| Arrow Cryogenic Deflasher SME | Machine / Capability | Alternate deflash method only when available | `CRYO-1` is down and listed only as possible/alternate for `055 Deflash` | Level 3 | Medium |

## 6. Optional / Capability Available SMEs

| SME | SME Type | Why Optional | Supporting ShopContext Evidence | Source Depth | Confidence |
|---|---|---|---|---|---|
| Old Conair Dryer SME | Machine / Capability | Inactive asset with no current mapped operation | `UNKNOWN-7` is inactive, work center unknown, and no current mapped operation | Level 3 | Low |

## 7. Needs Review SMEs

| SME | SME Type | Why Needs Review | Supporting ShopContext Evidence | Source Depth | Confidence | Open Question |
|---|---|---|---|---|---|---|
| None | n/a | No generated SME requires blocking review from current `shop-reference.md` | n/a | n/a | n/a | n/a |

## 8. Machine / Capability SMEs Generated

| Machine / Capability SME | Related Operation(s) | Work Center(s) | Route Status | Confidence | Trigger Summary |
|---|---|---|---|---|---|
| Arburg Allrounder 470 SME | `040 Mold Parts` | `5200` | Required | High | `IM-110`, Arburg, primary press, injection molding |
| Nissei FNX180 SME | `040 Mold Parts` | `5200` | Required | Medium | `IM-220`, Nissei, backup press, injection molding |
| Wabash Genesis Compression Press SME | `035 Compression Mold` | `5210` | Required | High | `CM-50`, Wabash, compression molding |
| Matsui Dryer 1 SME | `020 Dry Material` | `5110` | Required | High | `DRY-1`, Matsui, nylon drying |
| Dri-Air Dryer 2 SME | `020 Dry Material` | `5110` | Required | High | `DRY-2`, Dri-Air, ABS dryer |
| Blue M Post Cure Oven SME | `045 Post Cure` | `5120` | Required | High | `OV-9`, Blue M, post cure, oven |
| Arrow Cryogenic Deflasher SME | `055 Deflash` alternate | `5300` | Conditional | Medium | `CRYO-1`, cryogenic deflash, alternate |
| Trim Bench SME | `050 Trim/Gate`; `055 Deflash` | `5300` | Required | High | `BENCH-TRIM`, hand trim, hand deflash |
| Vision Gauge 500 SME | `060 Inspect`; `065 Check` conditional | `5400` | Required | High | `QC-1`, optical inspection, dimensional checks |
| Granite Surface Plate SME | `060 Inspect`; `065 Check` | `5400` | Required | High | `QC-2`, granite plate, manual gauges |
| Zebra ZT411 Label Printer SME | `075 Pack/Label` | `5500` | Required | High | `LBL-1`, label print, pack label |
| Old Conair Dryer SME | none current | `Unknown` | Optional / Capability Available | Low | `UNKNOWN-7`, inactive dryer, Conair |
| MX-44A Mold SME | `030 Setup Mold`; `040 Mold Parts` | `5200` | Required | High | `MX-44A`, mold setup, housing mold |

## 9. Machines / Capabilities Not Tied To Routes

| Machine / Capability | SME | Status | Reason | Open Question |
|---|---|---|---|---|
| `UNKNOWN-7` Old Conair Dryer | Old Conair Dryer SME | Optional / Capability Available | Inactive dryer with unknown work center and no current mapped operation | Is this asset retired, retained as backup, or irrelevant to this shop flow? |

## 10. Ambiguous Machines / Capabilities

| Machine / Capability | SME | Why Ambiguous | Open Question |
|---|---|---|---|
| `CRYO-1` Arrow Cryogenic Deflasher | Arrow Cryogenic Deflasher SME | Listed as down and alternate only, not current normal method | When restored, should it become normal for high-volume `EL-SEAL-12` deflash or remain optional? |

## 11. Route-To-SME Mapping

| Operation | Work Center | Route Status | Related SME(s) | Notes |
|---|---|---|---|---|
| `010 Issue Resin` | `5100` | Standard | Shop Flow SME | Material issue, no dedicated machine SME |
| `020 Dry Material` | `5110` | Standard | Matsui Dryer 1 SME; Dri-Air Dryer 2 SME | Material-dependent dryer mapping |
| `030 Setup Mold` | `5200` | Standard | MX-44A Mold SME; Shop Flow SME | Mold setup supports injection molding |
| `040 Mold Parts` | `5200` | Standard | Arburg Allrounder 470 SME; Nissei FNX180 SME; MX-44A Mold SME | `IM-110` primary, `IM-220` approved backup |
| `050 Trim/Gate` | `5300` | Standard | Trim Bench SME | Manual trim and gate removal |
| `060 Inspect` | `5400` | Standard quality gate | Inspection SME; Vision Gauge 500 SME; Granite Surface Plate SME | First article and hourly checks |
| `070 Pack` | `5500` | Standard | Shop Flow SME | Bag and box packaging |
| `095 MRB Hold` | `9999` | Conditional | Inspection SME; Shop Flow SME | Conditional MRB/disposition only |
| `010 Issue Material` | `5100` | Standard | Shop Flow SME | Silicone lot issue |
| `025 Prep Compound` | `Unknown` | Standard with conditional skip/reduction | Shop Flow SME | Manual/material prep; no dedicated machine |
| `035 Compression Mold` | `5210` | Standard | Wabash Genesis Compression Press SME | Compression molding operation |
| `045 Post Cure` | `5120` | Standard | Blue M Post Cure Oven SME | Oven cure operation |
| `055 Deflash` | `5300` | Standard | Trim Bench SME; Arrow Cryogenic Deflasher SME | Current normal hand deflash; cryogenic alternate |
| `065 Check` | `5400` | Standard quality gate | Inspection SME; Granite Surface Plate SME; Vision Gauge 500 SME | Primarily `QC-2`, `QC-1` when optical checks required |
| `075 Pack/Label` | `5500` | Standard | Zebra ZT411 Label Printer SME | Packaging label print |

## 12. Inspection Coverage

| Inspection / Test / Acceptance Point | Coordinator SME | Named Machine / Capability SME(s) | Supporting Evidence | Confidence |
|---|---|---|---|---|
| `PL-HOUSING-44` `060 Inspect` | Inspection SME | Vision Gauge 500 SME; Granite Surface Plate SME | Quality gate for first article and hourly checks | High |
| `EL-SEAL-12` `065 Check` | Inspection SME | Granite Surface Plate SME; Vision Gauge 500 SME when optical checks required | Quality gate for visual and dimensional inspection | High |
| `PL-HOUSING-44` `095 MRB Hold` | Inspection SME | none named | Conditional MRB/disposition operation | Medium |

## 13. Records Coverage By SME

| SME | Records This SME Would Ask For | Records Confirmed By Source | Notes |
|---|---|---|---|
| Shop Flow SME | Router, traveler, work order, operation status, material configuration | None | `shop-reference.md` defines planned flow only |
| Inspection SME | First article record, hourly inspection record, dimensional results, acceptance criteria | None | Records are useful but not confirmed as retained |
| Machine / Capability SMEs | Setup sheets, machine logs, run records, inspection results, labels, cure records as applicable | None | No actual records or logs were provided |

## 14. Document Gaps By SME

| SME | Documents That Would Level This SME Up | Why Needed |
|---|---|---|
| All machine/capability SMEs | Manuals, work instructions, setup sheets, process specs, acceptance criteria | Required for Level 4 technical answering |
| Inspection SME | Inspection plans, gauge instructions, sampling plans, customer acceptance criteria | Required to answer accept/reject or criteria questions |
| Shop Flow SME | Router control procedure, traveler examples, MRB procedure | Required to answer procedural and routing edge cases |

## 15. Router Readiness Summary

- Can the future router identify relevant SMEs from this output? Yes.
- Which SMEs can contribute useful Level 3 input now? All required and conditional SMEs can contribute shop-reference-supported context.
- Which SMEs are weak because they lack manuals/specs/evidence? All SMEs remain technical shells until Level 4/5 documents or evidence are added.
- Which routing triggers are missing or unclear? Old Conair Dryer current relevance and future `CRYO-1` normal-use status are unclear.
- Which open questions should be resolved before router testing? None are blocking; optional questions are listed for later enrichment.
- Are routing triggers broad enough to support plain-language user questions, not just exact shop jargon? Yes; profile shells include exact and semantic triggers.

## 16. Plain-Language Routing Check

| Plain-Language User Wording | Candidate SME(s) The Future Router Should Be Able To Select | Why |
|---|---|---|
| Which press made the housing? | Shop Flow SME; Arburg Allrounder 470 SME; Nissei FNX180 SME | Housing molding maps to `040 Mold Parts` and candidate presses |
| What dryer was used for nylon? | Matsui Dryer 1 SME; Shop Flow SME | Nylon drying maps to `DRY-1` |
| How are seals deflashed right now? | Trim Bench SME; Shop Flow SME; Arrow Cryogenic Deflasher SME | Current normal deflash uses trim bench; cryogenic deflash is alternate |
| Which gauge checks elastomer seals? | Inspection SME; Granite Surface Plate SME; Vision Gauge 500 SME | `065 Check` primarily uses `QC-2`, with `QC-1` when optical checks are required |
| Is MRB part of normal flow? | Shop Flow SME; Inspection SME | `095 MRB Hold` is conditional only |

## 17. Not Generated By Default

| SME / Area | Reason |
|---|---|
| Material Traceability SME | Not represented as a named machine/station/capability and not user-requested |
| MRB SME | `MRB Hold` is a conditional operation, but no named MRB station/capability was provided |
| Rework SME | No rework process or named rework station was provided |
| Maintenance / Equipment SME | Maintenance analysis is out of scope for SME Generator |
| Testing SME | No named test equipment or test operation was provided |

## 18. Open Questions

1. Is `UNKNOWN-7` Old Conair Dryer retired, retained as backup, or irrelevant to this shop flow?
2. When `CRYO-1` is restored, should it become normal for high-volume `EL-SEAL-12` deflash or remain optional?

## 19. Highest-Priority SMEs To Level Up First

| Priority | SME | Reason |
|---:|---|---|
| 1 | Inspection SME | Needed for quality gate interpretation, acceptance criteria, and inspection evidence requests |
| 2 | Arburg Allrounder 470 SME | Primary press for `PL-HOUSING-44` |
| 3 | Wabash Genesis Compression Press SME | Core machine for `EL-SEAL-12` molding |
| 4 | Trim Bench SME | Shared standard manual equipment for trim/gate and current deflash |
| 5 | Shop Flow SME | Coordinates product flow, standard-vs-conditional operations, and SME handoffs |
