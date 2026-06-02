# Knowledge Package: Manufacturing Operation Flow

## Package Purpose
This package gives the Shop Flow SME bounded context for routing, handoffs, normal-vs-conditional operations, and production-impact answers.

## Applies To
Shop Flow SME, Inspection SME, Arburg Allrounder 470 SME, Nissei FNX180 SME, Wabash Genesis Compression Press SME, packaging and inspection SMEs.

## Knowledge Level
Domain-general manufacturing flow knowledge with shop-specific generated mapping.

- Input Mapping Confidence: high
- Technical Source Confidence: low
- Source tier coverage: generated SME shells and shop-reference.md

## Process Overview
Manufacturing operation flow describes the planned sequence of work centers, machines, manual steps, inspection gates, and conditional holds. For this shop, `PL-HOUSING-44` includes material drying, molding, inspection, and packing. `EL-SEAL-12` includes material prep, compression molding, post cure, deflash, inspection/check, and packing. `095 MRB Hold` is conditional and excluded from standard flow.

## Core Principles
Flow knowledge answers "where does work go next," "which operation owns this step," and "what happens when a normal resource is unavailable." It does not by itself define capacity, cycle time, acceptance criteria, or process recipes.

## Equipment / Tooling / System Principles
Flow interacts with machines, tooling, labor, inspection, packaging, and conditional disposition steps. Approved alternates such as `IM-220` reduce routing risk but may still create schedule, setup, or queue impact.

## Machine-Specific Notes
Shop-specific facts: `IM-110` is primary press for `PL-HOUSING-44`; `IM-220` is approved backup. `CRYO-1` is alternate only when available; current normal deflash is `BENCH-TRIM`. `095 MRB Hold` is conditional only.

## Key Process Variables
Resource availability, setup/changeover time, queue, labor, material configuration, machine eligibility, inspection characteristic, and conditional hold status all affect flow.

## Process Window Concepts
Flow has operational margin when alternate resources exist. It has limited margin when only one approved resource exists, downstream gates are constrained, or conditional operations become active.

## Materials, Parts, Geometry, And Environment Interactions
Material configuration changes dryer route. Part family changes molding/inspection route. Seal geometry and flash condition affect deflash and inspection flow.

## Common Failure Modes
Potential flow issues include routing ambiguity, unavailable primary machine, backup queue conflicts, missing inspection criteria, conditional MRB confusion, and treating optional/alternate operations as standard.

## Failure Mechanisms
Flow breaks down when the selected route cannot be executed with available resources, when upstream conditions invalidate downstream assumptions, or when conditional steps are incorrectly included/excluded.

## Practical Heuristics
For outage impact, identify approved alternates first, then state remaining unknowns: backup availability, setup time, capacity, queue, staffing, and quality confirmation. For MRB, keep it conditional unless records show activation.

## Troubleshooting Logic
Separate routing questions from technical process questions. Route to machine/process/inspection SMEs when the answer depends on equipment behavior or product criteria.

## Important Terminology
- Standard flow: normal operation sequence.
- Conditional operation: step used only when triggered by condition or disposition.
- Approved backup: valid alternate resource for a normal operation.
- Work center: area/owner of operation execution.

## What This Package Can Help With
It supports concise answers about production flow and impact framing.

## What This Package Cannot Prove
It cannot prove actual schedule impact, WIP location, machine status, capacity, root cause, or acceptance.

## Source Map
Technical Source Confidence: low because this is mostly generated shop mapping, not public technical content. See `source-map.md`.
