# Machine-To-SME Mapping Rules

Machine / Capability SMEs are generated from named machines, stations, cells, equipment assets, benches, tooling areas, and major capabilities.

Do not map machines to broad task SMEs by default. The SME is usually named after the machine/capability itself.

## Mapping Procedure

1. Extract the exact machine/capability name from `shop-reference.md`.
2. Create an SME named after that item unless the source only provides a generic capability.
3. Link the SME to related operation numbers, operation names, work centers, and route status.
4. Classify status using `sme-status-classification-rules.md`.
5. Keep unmapped machines visible as Optional / Capability Available or Needs Review.

## Naming Examples

| Source Item | SME Name |
|---|---|
| `DEK Horizon` | DEK Horizon SME |
| `MY200` | MY200 SME |
| `VAC 545 Vapor Phase` | VAC 545 Vapor Phase SME |
| `Koh Young Zenith` | Koh Young Zenith SME |
| `Hioki Tester` | Hioki Tester SME |
| `Haas VF-2SS` | Haas VF-2SS SME |
| `Zeiss Contura G2` | Zeiss Contura G2 SME |
| `Low Pressure Molding Cell` | Low Pressure Molding Cell SME |
| `Harness Form Board Area` | Harness Form Board Area SME |
| unnamed CNC mill capability | CNC Mill SME |
| unnamed manual solder bench | Manual Soldering Bench SME |

## Status Rules

- Required: tied to a standard route operation.
- Conditional: tied only to conditional, alternate, special, rework, repair, MRB, or when-required use.
- Optional / Capability Available: listed in the source but not tied to standard flow.
- Needs Review: listed but unclear support, operation mapping, or capability.

## Inspection Machines

If the machine is an inspection/test/measurement asset, generate both:

- `Inspection SME`
- the named Machine / Capability SME

## Route Context Only

Area labels, line labels, and generic descriptors may remain route context only if the source explicitly says they are not separate machines or capabilities.

Example:

`Shared SMT Line` described as an area/line support label, not separate required machine -> route context only or Needs Review, not Required.

## Boundaries

- Do not create a separate Maintenance / Equipment SME by default.
- Do not create a separate Testing SME by default when a named tester exists; create the tester SME and let Inspection SME coordinate test handoff questions.
- Do not create broad process SMEs from machine keywords alone.
- Do not claim a machine is used in standard flow unless `shop-reference.md` supports it.
