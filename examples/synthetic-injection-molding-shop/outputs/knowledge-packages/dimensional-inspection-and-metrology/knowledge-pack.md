# Knowledge Package: Dimensional Inspection And Metrology

## Package Purpose
This package gives inspection SMEs technical context for choosing between manual/visual, granite surface plate/manual gauging, and optical/digital inspection methods.

## Applies To
Inspection SME, Granite Surface Plate SME, Vision Gauge 500 SME, Shop Flow SME, Arburg/Nissei molding SMEs as downstream context.

## Knowledge Level
Inspection-method knowledge.

- Input Mapping Confidence: high
- Technical Source Confidence: medium
- Source tier coverage: generated SME shells, ASME/NIST-style metrology sources, OEM optical comparator source

## Process Overview
Dimensional inspection compares a part or feature to a requirement using a defined measurement method. Manual/visual inspection is useful for presence, obvious condition, gross defects, and operator judgment. Granite surface plate inspection provides a stable reference plane for height, flatness, layout, and manual gauging. Optical/digital comparison supports edge, profile, and CAD-overlay style checks when the characteristic is visible and suitable for optical measurement.

## Core Principles
Inspection method should follow the characteristic, tolerance, part geometry, required uncertainty, operator dependence, throughput, and controlling criteria. A better method is not universally "manual" or "granite"; it is the method that can measure the required characteristic with adequate resolution, repeatability, traceability, and practicality.

## Equipment / Tooling / System Principles
Granite plates serve as stable datum surfaces for contact measurement. Height gauges, indicators, blocks, fixtures, and hand tools often depend on the plate and setup. Optical comparators use magnification, imaging, lighting, and sometimes CAD comparison to inspect edges/profiles without the same contact setup.

## Machine-Specific Notes
Shop-specific facts: `QC-2 Granite Surface Plate` is primary/manual inspection context for `EL-SEAL-12` `065 Check`; `QC-1 Vision Gauge 500` is used when optical dimensional checks are required. For `PL-HOUSING-44` `060 Inspect`, both `QC-1` and `QC-2` can be valid depending on inspection characteristic.

## Key Process Variables
- Characteristic type: flatness/height/location/profile/edge/visual condition determines method fit.
- Tolerance and uncertainty: tighter requirements need controlled methods and traceability.
- Datum scheme and fixturing: define how the part is oriented and measured.
- Operator technique: affects manual repeatability and visual consistency.
- Lighting and edge contrast: affect optical measurement quality.
- Surface condition and cleanliness: affect both contact and optical methods.
- Calibration status: affects whether measurement results can be trusted.

## Process Window Concepts
Inspection has a measurement window: the method must be capable enough relative to tolerance and stable enough for normal variation. If a characteristic is qualitative, manual/visual may be acceptable. If it is dimensional and datum-dependent, granite or optical methods may be stronger. If it is edge/profile-heavy and CAD-based, the VisionGauge-style method may be better.

## Materials, Parts, Geometry, And Environment Interactions
Flexible or elastomeric parts can deform under contact force, making fixturing and method selection critical. Molded plastic housings can be sensitive to datum choice and cooling-related warp. Temperature, cleanliness, burrs/flash, surface finish, and lighting can all bias inspection.

## Common Failure Modes
- False confidence from visual-only inspection when a dimensional tolerance is actually being judged.
- Poor repeatability from unstable fixturing or operator technique.
- Contact-force deformation on soft parts.
- Optical edge ambiguity from poor contrast, translucent material, flash, or surface condition.
- Bad results from out-of-calibration plates/gauges or undocumented datum setup.

## Failure Mechanisms
Measurement error comes from reference error, instrument error, setup error, operator error, environmental effects, and part interaction. Granite plates reduce some reference-plane error when calibrated and used correctly; optical systems reduce some contact/operator effects but can introduce lighting, focus, calibration, and edge-detection sensitivity.

## Practical Heuristics
Use manual/visual for obvious condition or gross feature presence. Use granite/manual gauging when the question depends on a physical datum plane, height, flatness, or layout-style checks. Use VisionGauge/optical methods when the characteristic is edge/profile/feature geometry suited to imaging and when optical checks are required. Ask for the inspection characteristic before declaring one method better.

## Troubleshooting Logic
When inspection answers disagree, separate part variation from method variation. Compare datum setup, fixture, operator, calibration, environmental conditions, and whether the two methods are actually measuring the same characteristic.

## Important Terminology
- Datum: reference feature or plane used to orient measurement.
- Uncertainty: quantified doubt around a measurement result.
- Repeatability: same operator/equipment getting consistent results.
- Reproducibility: different operators/equipment getting consistent results.
- Traceability: connection of calibration to recognized standards.

## What This Package Can Help With
It strengthens answers about what the granite plate is for, when optical inspection may be better, and why method selection depends on the characteristic rather than preference.

## What This Package Cannot Prove
It cannot prove pass/fail status, acceptance criteria, calibration status, actual measurement results, or an authorized replacement method.

## Source Map
Technical Source Confidence: medium. Strongest support is standards/OEM-style metrology context; weakest area is shop-specific inspection plans. See `source-map.md`.
