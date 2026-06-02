# Knowledge Package: Granite Surface Plate Metrology

## Package Purpose
This package gives the Granite Surface Plate SME technical depth on why a granite plate is used, what it can measure, and when another inspection method may be better.

## Applies To
Granite Surface Plate SME, Inspection SME, Vision Gauge 500 SME as alternate-method context.

## Knowledge Level
Inspection-method knowledge with standards-supported public context.

- Input Mapping Confidence: high
- Technical Source Confidence: high
- Source tier coverage: generated SME shells, ASME surface plate standard summary, NIST dimensional metrology context, Mitutoyo educational source

## Process Overview
A granite surface plate is a stable, flat reference plane used for layout, height measurement, flatness checks, fixture setup, and manual dimensional inspection. It gives the inspector a physical datum surface from which other tools can reference part height, location, or flatness.

## Core Principles
The value of a surface plate is not that it measures by itself; it provides a known reference surface for measurement systems. The plate’s usefulness depends on flatness, repeatability, cleanliness, support, calibration, environmental stability, and the gauge/fixture used with it.

## Equipment / Tooling / System Principles
Typical plate-based inspection may use height gauges, dial/test indicators, gauge blocks, angle plates, V-blocks, fixtures, and layout tools. The plate must be supported correctly and kept clean because dirt, burrs, or damaged spots can bias measurements. Calibration/recertification establishes whether the plate remains suitable for its intended grade and use.

## Machine-Specific Notes
Shop-specific facts: `QC-2 Granite Surface Plate` is the primary/manual inspection path for `EL-SEAL-12` `065 Check`; `PL-HOUSING-44` `060 Inspect` may use `QC-2` depending on the inspection characteristic. Public sources do not prove the shop plate grade, size, calibration date, or fixture setup.

## Key Process Variables
- Plate grade/flatness: affects reference quality.
- Local wear and repeatability: affect measurements even if overall plate condition seems acceptable.
- Support and leveling: affect plate behavior under load.
- Temperature and thermal gradients: affect parts, gauges, and reference stability.
- Cleanliness: chips, flash, dust, oil, or burrs can create false readings.
- Fixture and contact force: matter especially for soft or flexible parts.
- Gauge calibration: plate accuracy is only one part of the measurement chain.

## Process Window Concepts
Granite plate inspection is strong when the characteristic needs a physical datum plane and contact/manual gauging is appropriate. It is weaker for complex optical profiles, fine edge features, high-throughput automated checks, or soft parts that deform under contact unless fixturing is controlled.

## Materials, Parts, Geometry, And Environment Interactions
Elastomeric seals can deform under gravity or gauge force, so granite/manual inspection must control fixture and contact method. Molded housings may use plate checks for height/flatness or datum-based dimensional checks, but optical inspection may be better for edge/profile features.

## Common Failure Modes
- Measuring from a dirty or worn plate area can bias results.
- Using the wrong datum setup can answer the wrong question.
- Contact force can deform soft parts.
- A calibrated plate with uncalibrated gauges still leaves the measurement chain weak.
- Visual/manual judgment can be inconsistent if criteria are not defined.

## Failure Mechanisms
Reference-plane error propagates into height and flatness measurements. Local plate wear creates repeatability issues. Thermal expansion changes part and gauge dimensions. Fixture instability changes datum contact. Operator technique changes contact force and reading interpretation.

## Practical Heuristics
For "what is it used for," answer: stable reference-plane inspection and manual gauging. For "is there a better alternative," ask what characteristic is being checked. VisionGauge/optical inspection may be better for profile/edge/CAD-comparison checks; CMM or dedicated fixtures may be better for complex 3D geometry; granite remains appropriate for simple datum-based manual checks.

## Troubleshooting Logic
When granite and optical results differ, compare the characteristic definition, datum setup, calibration status, part support, contact force, lighting/edge detection, and whether both methods are measuring the same feature.

## Important Terminology
- Surface plate: flat reference plane used in inspection/layout.
- Plate grade: accuracy class for flatness and repeatability.
- Recertification: periodic verification of plate condition.
- Local variation: small-area error that can affect repeated measurements.
- Datum setup: how the part is supported and referenced.

## What This Package Can Help With
It supports better answers about granite plate purpose, limitations, method selection, and alternatives such as optical comparators or CMMs.

## What This Package Cannot Prove
It cannot prove the shop plate is calibrated, the inspection method is approved for a characteristic, or a part passes/fails.

## Source Map
Technical Source Confidence: high for general surface-plate metrology, low for shop-specific status. See `source-map.md`.
