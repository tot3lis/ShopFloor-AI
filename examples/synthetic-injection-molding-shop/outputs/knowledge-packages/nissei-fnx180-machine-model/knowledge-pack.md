# Knowledge Package: Nissei FNX180 Machine Model

## Package Purpose
This package gives the Nissei FNX180 SME public model context for `IM-220`, the approved backup press for `PL-HOUSING-44`.

## Applies To
Nissei FNX180 SME, Arburg Allrounder 470 SME, Injection Molding Process package, Shop Flow SME.

## Knowledge Level
Machine/model-specific public knowledge.

- Input Mapping Confidence: high
- Technical Source Confidence: high
- Source tier coverage: generated SME shell, public OEM Nissei FNX180 specifications

## Process Overview
The shop-specific SME shell identifies `IM-220 Nissei FNX180` as the approved backup press for `PL-HOUSING-44` `040 Mold Parts`. Public Nissei specifications identify the FNX180 as a hybrid injection molding machine model with published clamping-force context. That supports model-level reasoning about the backup press as an actual injection press, while leaving shop setup and approval criteria outside public knowledge.

## Core Principles
A backup press reduces production vulnerability when the primary is unavailable, but it does not automatically eliminate impact. The backup must be available, tooled, staffed, set up, and quality-confirmed for the job. Machine-model public data helps identify capability class; shop data is required for process equivalence.

## Equipment / Tooling / System Principles
The FNX180 is part of Nissei's injection molding equipment family. Relevant equipment considerations include clamp capacity, injection unit/screw configuration, controller behavior, mold mounting, ejection, and auxiliary equipment integration.

## Machine-Specific Notes
Public OEM support exists for FNX180 specifications. The generated SME shell supports that this exact named model is the shop backup. Public data does not prove screw diameter, options, maintenance state, or `MX-44A` setup qualification.

## Key Process Variables
- Clamp capability: affects mold closure and parting-line control.
- Shot/injection unit configuration: affects material residence, pressure, velocity, and fill capability.
- Setup transfer: affects whether primary-press settings can be translated safely.
- Mold compatibility: affects mounting, ejection, water/temperature connections, and safety.
- Availability and queue: affect production impact when `IM-110` is down.

## Process Window Concepts
An approved backup indicates the shop has a defined alternate normal candidate. The production effect of losing `IM-110` depends on whether `IM-220` can absorb the work without delaying other jobs and whether setup/quality checks are current.

## Materials, Parts, Geometry, And Environment Interactions
The backup press interacts with the same resin drying, mold tooling, part geometry, cooling, and inspection requirements as the primary path. Different press dynamics can still change process sensitivity even when the job is approved.

## Common Failure Modes
Generic backup-transfer risks include setup mismatch, longer changeover, different pressure/velocity response, auxiliary mismatch, and schedule conflicts. These can be associated with production delay or extra confirmation work, but are not evidence of quality loss.

## Failure Mechanisms
The mechanism of impact from a primary press outage is operational: the normal route loses capacity and the job must move to backup, wait, or be rescheduled. The mechanism of possible process difference is technical: press response, screw/injection configuration, clamp behavior, and auxiliary setup can shift the molding window.

## Practical Heuristics
Treat `IM-220` as a valid normal candidate, not an emergency guess. Still distinguish "approved backup exists" from "zero production impact"; the latter requires real schedule, queue, setup time, and capacity records.

## Troubleshooting Logic
If a symptom appears only after moving to `IM-220`, consider setup-transfer and machine-response differences, but compare material, mold, operator, timing, and inspection data before making a cause claim.

## Important Terminology
- Approved backup press: a valid alternate candidate when primary press is unavailable or scheduling requires it.
- Setup transfer: moving a job's tooling/process context from one press to another.
- Capability class: general model capability, not shop approval.

## What This Package Can Help With
It supports SME answers about backup-press implications, production routing resilience, and conservative machine-model context for `IM-220`.

## What This Package Cannot Prove
It cannot prove backup availability, actual cycle time, process equivalence, installed options, maintenance condition, root cause, corrective action, or acceptance.

## Source Map
Technical Source Confidence: high for public model identity/spec context, lower for shop execution. See `source-map.md`.
