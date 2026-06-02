# SME Taxonomy

This file is not a fixed taxonomy and not a complete allowed SME universe.

The SME Generator primarily creates:

- `Shop Flow SME`
- `Inspection SME`
- Machine / Capability SMEs named from `shop-reference.md`
- User-requested SMEs

Use this file only as a small set of naming examples. Do not use it to create default task/process SMEs.

## Always Generated

| SME | Source Type | Notes |
|---|---|---|
| Shop Flow SME | Shop flow | Always generated from route/operation/work-center context. |
| Inspection SME | Inspection coordinator | Always generated; coordinates inspection/test/acceptance-document questions. |

## Machine / Capability Naming Examples

| Source Pattern | Example SME |
|---|---|
| named stencil printer | DEK Horizon SME |
| named placement machine | MY200 SME |
| named AOI machine | Koh Young Zenith SME |
| named vapor phase machine | VAC 545 Vapor Phase SME |
| named electrical tester | Hioki Tester SME |
| named CNC mill | Haas VF-2SS SME |
| named CMM | Zeiss Contura G2 SME |
| named crimp press | TE AMP-O-LECTRIC Model G SME |
| named harness test station | Cirris 1100H+ SME |
| named autoclave | Autoclave AC-7 SME |
| named paint booth | Paint Booth PB-3 SME |
| named layup table | Layup Table 1 SME |
| named repair equipment used only conditionally | Repair Hot Bonder SME |
| unnamed but major capability | CNC Mill SME, Manual Soldering Bench SME, Harness Test Station SME |

## Boundary

These examples only normalize names. They do not add technical process knowledge, root cause logic, corrective action, SPC analysis, machine performance analysis, web scraping, or vector DB behavior.
