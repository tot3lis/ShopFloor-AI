# Machine / Capability SME Rules

Machine / Capability SMEs are the primary generated SME type.

Start from named machines, equipment assets, stations, cells, benches, tooling areas, test stations, inspection machines, and major capabilities in `shop-reference.md`.

Create one SME candidate for each named machine, station, cell, equipment asset, or major capability that appears in:

- Machine / Equipment Dictionary
- Machine-To-Operation Map
- Work Center Dictionary associated machine/equipment fields
- Operation Step Summaries equipment/station lists
- Shop-Specific Terminology
- Open Mapping Questions

Do not generate separate process/task SMEs from every operation by default.

## Naming

Prefer the source name when it is specific:

- `DEK Horizon` -> `DEK Horizon SME`
- `MY200` -> `MY200 SME`
- `VAC 545 Vapor Phase` -> `VAC 545 Vapor Phase SME`
- `Koh Young Zenith` -> `Koh Young Zenith SME`
- `Zeiss Contura G2` -> `Zeiss Contura G2 SME`
- `Paint Booth PB-3` -> `Paint Booth PB-3 SME`

Use capability names only when the source gives a capability but not a uniquely named asset:

- `Manual Soldering Bench SME`
- `CNC Mill SME`
- `Harness Test Station SME`
- `Inspection Bench SME`
- `Bonding Station SME`

## Required Profile Content

Each Machine / Capability SME should include:

- machine/capability name
- related operation numbers
- related operation names
- related work centers
- standard route status
- supported process/capability
- likely records named or implied by the source
- manuals/specs/work instructions that would make the shell stronger later
- maintenance/documents that may become part of a future knowledge package
- answer boundaries
- open questions
- exact/named routing triggers
- semantic/plain-language routing triggers
- router contribution format

## Router Trigger Guidance

Exact / Named Triggers should include the machine/capability name, aliases, related operation numbers, operation names, work centers, named records, and named documents.

Semantic / Plain-Language Triggers should describe what the machine/capability does in user language. Use only relevant terms.

Examples:

- heat-process machines: oven, heat, heating, thermal process, profile, recipe, parts moving during heat, components shifting, load size, chamber
- placement machines: placement, placed parts, component placement, feeder, nozzle, program, component location
- print machines: paste, solder paste, print, stencil, paste deposit, smear, aperture, squeegee
- inspection machines: AOI, camera inspection, inspection image, defect photo, before/after evidence, visual check, escape
- machining machines: machining, cut, mill, drill, tap, toolpath, program, setup, fixture, dimension, tolerance
- harness machines: crimp, wire, harness, pull test, continuity, connector, terminal, pin, wire prep
- paint/coating machines: paint, primer, coating, spray, cure, booth, mask, finish
- composite/cure machines: layup, cure, autoclave, vacuum bag, pressure, temperature, resin, ply, delamination

## Boundaries

- Do not add deep technical process knowledge.
- Do not diagnose root cause.
- Do not recommend corrective action.
- Do not analyze machine performance.
- Do not claim actual execution history unless actual records are provided.
- Do not create a separate Maintenance / Equipment SME by default; maintenance documents belong inside each machine/capability shell as future uploads.
