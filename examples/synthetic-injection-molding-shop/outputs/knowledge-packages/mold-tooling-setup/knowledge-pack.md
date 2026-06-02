# Knowledge Package: Mold Tooling Setup

## Package Purpose
This package gives the MX-44A Mold SME general tooling/setup context for injection molding without pretending to know the actual mold design.

## Applies To
MX-44A Mold SME, Arburg Allrounder 470 SME, Nissei FNX180 SME, Injection Molding Process package.

## Knowledge Level
Equipment-family/tooling knowledge.

- Input Mapping Confidence: high
- Technical Source Confidence: low
- Source tier coverage: generated SME shell, general injection molding process context

## Process Overview
Injection mold setup installs and prepares a mold so the press can fill, pack, cool, eject, and repeat consistently. The shop-specific generated context names `MX-44A` as the mold/tooling associated with `PL-HOUSING-44` molding.

## Core Principles
Mold setup depends on mounting, alignment, clamp interface, ejection, water/cooling, heaters if present, vents, gates, parting surfaces, safety, and process setup. Tooling condition can influence flash, short shots, dimensions, surface condition, and ejection.

## Equipment / Tooling / System Principles
The mold defines cavity geometry, runners/gates, venting, parting line, cooling, and ejection. The press supplies clamp/injection/control. The dryer and material system supply conditioned resin.

## Machine-Specific Notes
No public or uploaded source covers exact `MX-44A`. Keep all mold/tooling content generic and treat exact mold facts as unknown except its shop mapping to `PL-HOUSING-44`.

## Key Process Variables
Mold alignment, clamp seating, parting-line condition, vent cleanliness, gate/runner condition, cooling circuit condition, ejection action, setup repeatability, and press compatibility.

## Process Window Concepts
The same mold on two approved presses may still need setup confirmation because clamp/injection behavior and auxiliary connections can differ. Tooling fit does not prove process equivalence.

## Materials, Parts, Geometry, And Environment Interactions
Molded housing geometry, resin selection, cooling, and ejection all interact. Nylon vs ABS/general resin may affect shrinkage, cooling, and process sensitivity.

## Common Failure Modes
Tooling-related contributors may include flash at worn parting lines, short shots from vent/gate restrictions, dimensions from cooling/ejection variation, surface defects from cavity condition, or sticking/ejection marks.

## Failure Mechanisms
Mold surfaces, vents, gates, cooling, and ejection convert process energy into final part shape. Small tooling condition changes can appear as process or inspection problems.

## Practical Heuristics
When a question involves both `IM-110` and `IM-220`, include `MX-44A` as a context package because mold setup/fit can matter to backup use. Do not invent mold details.

## Troubleshooting Logic
Separate press effects from mold effects by comparing whether symptoms follow the mold across presses or remain with a press independent of mold/tooling.

## Important Terminology
- Parting line: mold split interface where flash can occur.
- Gate: entry point for molten resin.
- Vent: path for air/gas escape.
- Ejection: removal of molded part.

## What This Package Can Help With
It strengthens questions and reasoning around press-to-mold interaction and why exact mold records matter.

## What This Package Cannot Prove
It cannot prove mold design, condition, approved setup, compatibility limits, root cause, corrective action, or acceptance.

## Source Map
Technical Source Confidence: low because no exact mold source is available. See `source-map.md`.
