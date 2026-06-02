# Knowledge Package: Resin Drying And Material Conditioning

## Package Purpose
This package gives dryer/material SMEs process-subtype knowledge about nylon and ABS/general resin drying before molding `PL-HOUSING-44`.

## Applies To
Matsui Dryer 1 SME, Dri-Air Dryer 2 SME, Old Conair Dryer SME, Injection Molding Process package, Arburg/Nissei press SMEs.

## Knowledge Level
Process-subtype and material-family knowledge.

- Input Mapping Confidence: high
- Technical Source Confidence: medium
- Source tier coverage: generated SME shells, public dryer/resin-moisture technical sources

## Process Overview
Resin drying removes or controls moisture before molding so material enters the press within a usable condition. The shop-specific context says `DRY-1 Matsui Dryer 1` is used for nylon resin and `DRY-2 Dri-Air Dryer 2` is used for ABS/general resin. `PL-HOUSING-44` may use either nylon or ABS depending on customer/material configuration.

## Core Principles
Moisture affects resin differently by material. Hygroscopic materials absorb moisture from air, and moisture can create cosmetic defects, bubbles/splay, hydrolysis, degraded mechanical properties, or process instability. Dryer performance depends on temperature, air dryness/dew point, airflow, residence time, material loading, and preventing reabsorption after drying.

## Equipment / Tooling / System Principles
Common drying systems use heated air, desiccant/dehumidified air, hopper residence, and material handling controls. A dryer can only support molding quality if it is matched to resin requirement, loaded correctly, maintained, and connected to the molding process without letting material regain moisture.

## Machine-Specific Notes
The SME shells name `DRY-1`, `DRY-2`, and `OLD-DRY`. No exact public model manuals were gathered for those shop assets. Keep dryer-machine claims at shop-mapping level only.

## Key Process Variables
- Resin family and grade: defines whether drying is required and what target moisture may be.
- Initial moisture: affects drying time and risk.
- Drying temperature and time: influence moisture removal and degradation risk.
- Dew point/air dryness: affects drying capacity.
- Airflow and hopper loading: affect whether pellets see uniform drying.
- Transfer exposure: affects reabsorption before molding.
- Material lot and packaging: affect incoming condition.

## Process Window Concepts
A drying window balances enough moisture removal against overheating, contamination, and unnecessary dwell. Supplier data for the exact resin grade should control numeric targets. Public sources support the concept, not shop recipe values.

## Materials, Parts, Geometry, And Environment Interactions
Nylon generally has stronger moisture sensitivity than many general-purpose resins. ABS may still require drying depending on grade, storage, and supplier instruction. Humid environments and open containers can shorten the usable time after drying.

## Common Failure Modes
Wet or poorly conditioned resin may be associated with splay, bubbles, voids, silver streaking, poor surface appearance, degraded mechanical properties, inconsistent fill, or dimensional instability. Overheating or excessive residence can also damage some materials.

## Failure Mechanisms
Water can vaporize during melt processing and create bubbles or streaks. For susceptible polymers, moisture can chemically break polymer chains during processing. Uneven dryer performance can create lot-to-lot or hopper-position variation.

## Practical Heuristics
Tie dryer selection to material configuration: nylon to `DRY-1`, ABS/general to `DRY-2`. Treat `OLD-DRY` as historical/backup context only if the SME shell says so. Ask for resin data sheet, dryer recipe, and moisture records before declaring material acceptable.

## Troubleshooting Logic
If a molding symptom appears material-like, separate resin grade, material lot, dryer used, hopper residence, dew point/temperature records, transfer exposure, and press/tooling changes. Do not assume a dryer caused the issue without records.

## Important Terminology
- Hygroscopic: absorbs moisture from ambient air.
- Dew point: measure of air dryness used in drying systems.
- Residence time: time material spends in dryer/hopper.
- Reabsorption: material taking moisture back after drying.

## What This Package Can Help With
It strengthens SME answers about dryer mapping, why nylon/ABS drying matters, and what source depth is missing for material-specific decisions.

## What This Package Cannot Prove
It cannot prove actual moisture level, approved drying recipe, material acceptability, dryer health, root cause, corrective action, or inspection disposition.

## Source Map
Technical Source Confidence: medium. See `source-map.md`.
