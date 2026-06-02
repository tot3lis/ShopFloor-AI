# Knowledge Package: Injection Molding Process

## Package Purpose
This package gives injection molding SMEs deeper process-family knowledge for thermoplastic molding questions involving `PL-HOUSING-44`, `IM-110`, `IM-220`, and `MX-44A`.

## Applies To
Arburg Allrounder 470 SME, Nissei FNX180 SME, MX-44A Mold SME, Shop Flow SME, Matsui Dryer 1 SME, Dri-Air Dryer 2 SME, and Inspection SME.

## Knowledge Level
Process-family knowledge.

- Input Mapping Confidence: high
- Technical Source Confidence: medium
- Source tier coverage: generated SME shells, shop-reference.md, OEM press context, public process/trade guidance

## Process Overview
Injection molding melts thermoplastic resin, pushes it into a closed mold under controlled pressure and velocity, packs the cavity as material shrinks, cools the part until it can hold shape, then ejects it for downstream operations. In this shop, `PL-HOUSING-44` `040 Mold Parts` normally runs on `IM-110` Arburg Allrounder 470, with `IM-220` Nissei FNX180 as an approved backup when the primary press is unavailable or scheduling requires it.

## Core Principles
The molded part is controlled by the material state, the mold cavity and venting, the press clamp/injection system, cooling, and the inspection characteristic being evaluated. Filling problems, packing problems, cooling problems, and material-conditioning problems can create similar visible symptoms, so this package supports separation of possibilities rather than root-cause assignment.

Clamp force keeps the mold closed against cavity pressure. Too little effective clamp margin can be associated with flash; excessive or poorly applied clamp can affect venting or tooling stress. Injection velocity and pressure influence how the melt fronts fill the cavity. Pack/hold behavior compensates for shrinkage while the gate remains effective. Cooling time, mold temperature, and part geometry influence dimensional stability and warpage.

## Equipment / Tooling / System Principles
An injection molding press combines a plasticizing/injection unit, clamping unit, mold mounting platens, machine controls, and auxiliary equipment such as dryers and temperature control. The mold defines cavity shape, gate/runner behavior, venting, parting line, ejection, and critical geometry. The press provides repeatable motion, force, heating, injection, hold, and ejection control.

## Machine-Specific Notes
Shop-specific facts from the SME shell: `IM-110` is the primary press for `PL-HOUSING-44` `040 Mold Parts`; `IM-220` is an approved backup press. Public sources support close model context for the ARBURG 470 H family and exact public model context for Nissei FNX180, but those sources do not prove shop configuration, tooling compatibility limits, setup sheet values, cycle time, or backup equivalency.

## Key Process Variables
- Material moisture and drying state: can affect splay, bubbles, degradation, fill behavior, and mechanical properties, especially for hygroscopic materials such as nylon and ABS-family resins.
- Melt temperature and residence: affect viscosity, flow, degradation risk, color stability, and packing behavior.
- Mold temperature and cooling: affect shrinkage, warpage, surface appearance, crystallinity for semi-crystalline materials, and ejection stability.
- Injection velocity and pressure: affect fill balance, shear heat, burn risk, short-shot risk, and flash sensitivity.
- Pack/hold pressure and time: affect sink, voids, dimensions, and gate freeze behavior.
- Clamp force and mold alignment: affect parting-line control, flash, venting, tooling stress, and repeatability.
- Tooling condition: affects parting line, vents, gates, ejection, surface marks, and dimensional behavior.
- Press selection: primary vs backup press can change setup effort, scheduling flexibility, process matching, and validation burden.

## Process Window Concepts
A stable molding window has enough margin for normal variation in material lot, moisture, machine response, mold temperature, and ambient conditions. A narrow window may make small changes appear as intermittent defects. Moving a mold from primary to backup press can require setup confirmation because press dynamics, screw/injection unit, clamp behavior, and control response may differ even when both presses are approved candidates.

## Materials, Parts, Geometry, And Environment Interactions
Nylon and ABS/general resin are both listed as valid material-dependent candidates for `PL-HOUSING-44`, but they should not be treated as interchangeable process-wise. Nylon moisture behavior can be more severe and can change mechanical behavior; ABS also benefits from moisture control where supplier guidance requires it. Geometry such as ribs, bosses, wall-thickness transitions, gates, and long flow paths can amplify sink, warp, weld-line, short-shot, and cooling sensitivity.

## Common Failure Modes
- Short shot may be associated with insufficient fill, cold material, restricted gates/vents, low shot size, or machine/recipe mismatch.
- Flash may be associated with excessive cavity pressure, inadequate clamp margin, worn/damaged parting line, vent issues, or poor mold seating.
- Sink and voids may be associated with insufficient packing, thick sections, gate freeze timing, or cooling imbalance.
- Warpage may be associated with nonuniform shrinkage, cooling imbalance, material orientation, ejection stress, or geometry.
- Splay, bubbles, and silver streaks may be associated with moisture, trapped gas, contamination, or thermal degradation.
- Dimensional variation may be associated with thermal stability, material lot variation, pack/cool variation, fixture or measurement method differences.

## Failure Mechanisms
Many molding defects are physical expressions of pressure, temperature, flow, shrinkage, and venting. For example, material that is too viscous for the selected fill strategy may resist complete cavity fill. Moisture can vaporize or degrade polymer chains during melt processing. Inadequate hold pressure can allow shrinkage to pull surfaces inward. Uneven cooling can lock different shrinkage levels into different part regions. These mechanisms explain plausible pathways, not actual root cause.

## Practical Heuristics
Experienced molding SMEs usually separate the question into material prep, press/mold setup, tooling condition, machine repeatability, and inspection method. For this shop, a primary-press-down question should first identify whether `IM-220` is available and approved for the same job, then treat remaining impact as schedule/setup/capacity risk until actual cycle-time and setup records are available.

## Troubleshooting Logic
Consider whether the symptom appears on one press or both candidate presses, whether it tracks to a material configuration, whether it begins after a setup/changeover, whether it appears in the same geometry, and whether the measurement method changed. Compare patterns rather than assuming the press caused the issue.

## Important Terminology
- Primary press: `IM-110` for `PL-HOUSING-44` `040 Mold Parts`.
- Approved backup press: `IM-220` for the same operation when primary is unavailable or scheduling requires it.
- Pack/hold: post-fill pressure phase used to compensate for shrinkage while the gate remains effective.
- Process window: operating range that produces acceptable output with normal variation.
- Flash: excess material at parting lines or gaps.
- Short shot: incomplete filling of the cavity.
- Splay: streaking often associated with moisture, gas, or degradation.

## What This Package Can Help With
It strengthens SME answers about press impact, backup-press implications, material-prep interactions, common molding symptoms, and what data would be needed to move from general reasoning to shop-specific conclusion.

## What This Package Cannot Prove
It cannot prove actual press settings, cycle time, capacity loss, setup equivalency, tooling condition, machine health, root cause, corrective action, or part acceptance.

## Source Map
Technical Source Confidence: medium. Strongest support is public OEM model context plus general process guidance. Weakest area is shop-specific setup/process data. See `source-map.md`.
