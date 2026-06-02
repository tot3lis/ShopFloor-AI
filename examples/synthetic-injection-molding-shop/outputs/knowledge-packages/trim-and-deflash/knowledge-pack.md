# Knowledge Package: Trim And Deflash

## Package Purpose
This package gives trim/deflash SMEs practical process knowledge for manual hand deflash and alternate cryogenic deflash of molded elastomer parts.

## Applies To
Trim Bench SME, Arrow Cryogenic Deflasher SME, Wabash Genesis Compression Press SME, Inspection SME.

## Knowledge Level
Process-subtype knowledge.

- Input Mapping Confidence: high
- Technical Source Confidence: medium
- Source tier coverage: generated SME shells, public cryogenic deflash vendor/process sources

## Process Overview
Deflash removes excess material left from molding, commonly at parting lines, gates, vents, or overflow areas. In this shop, `EL-SEAL-12` `055 Deflash` currently uses `BENCH-TRIM Trim Bench` for hand deflash because `CRYO-1 Arrow Cryogenic Deflasher` is down. `CRYO-1` is only an alternate possible method when available.

## Core Principles
Deflash quality depends on part material, flash thickness, geometry, accessibility, tool/method, operator technique, and inspection criteria. Manual trim offers direct control and flexibility. Cryogenic deflash embrittles flash, often using liquid nitrogen and media/tumbling/blasting action, so thin flash can break away more readily.

## Equipment / Tooling / System Principles
Manual trim uses hand tools, benches, fixtures, magnification/lighting, and operator judgment. Cryogenic systems use low temperature, time, rotation/tumbling or blast media, and part loading to remove flash. Both methods need criteria to avoid over-trimming, residual flash, or part damage.

## Machine-Specific Notes
The generated shop context names `CRYO-1 Arrow Cryogenic Deflasher`, but no exact Arrow model source was gathered. Keep cryogenic content at process-family level.

## Key Process Variables
- Flash thickness and location: affects method fit.
- Part material and brittleness at low temperature: affects cryogenic response.
- Geometry/recesses: affect manual accessibility and cryogenic effectiveness.
- Operator technique/tool sharpness: affect manual repeatability.
- Cryogenic temperature/time/media/load: affect removal and part risk.
- Inspection criteria: define acceptable residual flash or edge condition.

## Process Window Concepts
Manual deflash is often better for low-volume, delicate, or judgment-heavy work. Cryogenic deflash may be better for repeatable high-volume flash removal where the part material and geometry respond well. The shop's current normal method is manual because the cryogenic equipment is down.

## Materials, Parts, Geometry, And Environment Interactions
Elastomer seals can have thin edges and functional sealing surfaces. Over-removal or nicking can be as problematic as residual flash. Cryogenic methods may access recesses that are slow by hand, but method suitability needs qualification.

## Common Failure Modes
Residual flash, nicks/cuts, rounded or damaged edges, dimensional change, surface damage, over-processing, and inconsistent operator results can occur depending on method.

## Failure Mechanisms
Manual defects come from tool contact, operator variation, access limits, and unclear criteria. Cryogenic defects can come from excessive cold exposure, media action, cycle conditions, or part geometry/material mismatch.

## Practical Heuristics
Answer current-state questions with `BENCH-TRIM` as normal method. Mention `CRYO-1` only as an alternate when available, not current normal production. Do not recommend switching without equipment status, qualification, and inspection criteria.

## Troubleshooting Logic
Separate molding flash creation from deflash removal quality. A deflash symptom may originate in the mold/process, the trim method, or inspection criteria.

## Important Terminology
- Flash: excess material from mold parting/overflow.
- Hand deflash: manual removal of flash.
- Cryogenic deflash: low-temperature process that embrittles flash before removal.
- Residual flash: flash left after deflash.

## What This Package Can Help With
It supports answers about current vs alternate deflash methods and why method choice depends on material, geometry, and equipment availability.

## What This Package Cannot Prove
It cannot prove `CRYO-1` availability, method approval, deflash acceptance, root cause, or corrective action.

## Source Map
Technical Source Confidence: medium. See `source-map.md`.
