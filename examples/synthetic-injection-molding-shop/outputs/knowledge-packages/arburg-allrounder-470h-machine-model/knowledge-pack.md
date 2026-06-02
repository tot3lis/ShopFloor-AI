# Knowledge Package: ARBURG ALLROUNDER 470 H Machine Model

## Package Purpose
This package gives the Arburg Allrounder 470 SME conservative public model-family context for `IM-110`, the primary press for `PL-HOUSING-44`.

## Applies To
Arburg Allrounder 470 SME, Injection Molding Process package, MX-44A Mold SME, and Shop Flow SME.

## Knowledge Level
Machine/model-specific public knowledge, used as close model-family context.

- Input Mapping Confidence: medium
- Technical Source Confidence: medium
- Source tier coverage: generated SME shell, public OEM ARBURG 470 H technical data

## Process Overview
The public ARBURG 470 H is a hybrid ALLROUNDER injection molding machine family. ARBURG describes it as combining servo-electric clamping behavior with a hydraulic injection unit. That context is useful for understanding how a press in this family may support precise and repeatable molding, but it does not prove the shop asset’s exact variant.

## Core Principles
Hybrid presses combine electric-axis precision and hydraulic injection capability. For SMEs, this means process behavior may involve clamp motion precision, injection response, machine controls, and mold/auxiliary integration. The important shop fact remains: `IM-110` is the primary candidate press for `PL-HOUSING-44`.

## Equipment / Tooling / System Principles
The press supports mold mounting, clamping, plasticizing, injection, hold/pack, cooling, and ejection. Tool fit, clamp behavior, injection-unit sizing, controller setup, and auxiliary interfaces can affect whether a given mold runs well on a given press.

## Machine-Specific Notes
Public source support is strongest for `ALLROUNDER 470 H`, while the generated shop SME names `IM-110 Arburg Allrounder 470`. Treat this as close machine-family context, not verified exact-asset data. Do not infer that the shop press has every option or performance variant shown in ARBURG public material.

## Key Process Variables
- Clamp capacity and platen/tie-bar geometry: affect mold compatibility and flash margin.
- Injection unit sizing: affects shot capacity, pressure/velocity capability, and residence behavior.
- Controller and axis response: affect repeatability, setup transfer, and cycle stability.
- Mold mounting and ejection compatibility: affect changeover and backup planning.
- Auxiliary integration: dryer, material feed, mold temperature, and automation can matter to production readiness.

## Process Window Concepts
The primary press being a preferred normal candidate means the process window is likely known around that press. If it is down, the shop can route to `IM-220`, but setup matching, schedule availability, and confirmation of part quality become the practical constraints. Public ARBURG data cannot quantify the lost capacity.

## Materials, Parts, Geometry, And Environment Interactions
The press context interacts with nylon/ABS resin condition, `MX-44A` tooling, part geometry, cooling, and inspection requirements. Public model data cannot tell whether a particular material/tooling combination is validated on the shop asset.

## Common Failure Modes
Machine-family issues can be associated with injection repeatability, clamp/mold seating, heater/control stability, screw/plasticizing condition, hydraulic/electric axis faults, and auxiliary interface problems. These are generic possibilities, not evidence that `IM-110` has any issue.

## Failure Mechanisms
Press-related mechanisms usually act through pressure/velocity delivery, temperature control, clamp behavior, or inconsistent cycling. A press outage affects production primarily by removing the normal path and forcing backup use, schedule reshuffle, or hold until the primary is restored.

## Practical Heuristics
For production-impact questions, separate capability from availability. `IM-220` being approved reduces single-point-of-failure risk, but does not eliminate changeover, queue, setup, or capacity impact. For quality questions, compare data from the primary and backup press before assigning machine contribution.

## Troubleshooting Logic
Consider whether the issue follows `IM-110`, follows `MX-44A`, follows material lots, or follows inspection characteristic. Press identity alone is not root-cause evidence.

## Important Terminology
- Hybrid press: machine architecture combining electric and hydraulic strengths.
- Clamp unit: mechanism that closes and holds the mold.
- Injection unit: plasticizes and injects molten resin.
- Primary press: shop-preferred normal press for a job.

## What This Package Can Help With
It supports bounded answers about what a primary press outage means, why backup qualification matters, and what press-family considerations may affect setup transfer.

## What This Package Cannot Prove
It cannot prove the exact `IM-110` variant, installed options, maintenance condition, cycle time, uptime, approved settings, root cause, or capacity loss.

## Source Map
Technical Source Confidence: medium. Strongest source is OEM ARBURG public technical data for the 470 H family; weakest area is exact shop asset configuration. See `source-map.md`.
