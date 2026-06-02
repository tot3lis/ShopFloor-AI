# Knowledge Package: VisionGauge 500 Optical Comparator

## Package Purpose
This package gives the Vision Gauge 500 SME public model-family context for optical/digital inspection questions.

## Applies To
Vision Gauge 500 SME, Inspection SME, Granite Surface Plate SME as alternate-method context.

## Knowledge Level
Machine/model-specific public knowledge.

- Input Mapping Confidence: high
- Technical Source Confidence: medium
- Source tier coverage: generated SME shell, public OEM VisionGauge 500 Series sources

## Process Overview
The VisionGauge 500 Series is a digital optical comparator family used to inspect part profiles and features by imaging the part and comparing it to CAD or defined measurement criteria. In this shop, `QC-1 Vision Gauge 500` is used for `PL-HOUSING-44` inspection characteristics as needed and for `EL-SEAL-12` only when optical dimensional checks are required.

## Core Principles
Optical inspection is strongest when the target feature is visible, has clear edge contrast, and can be compared to a digital profile, CAD nominal, or programmed measurement. It can reduce contact-force effects and operator overlay variation, but it introduces lighting, focus, calibration, and edge-detection sensitivity.

## Equipment / Tooling / System Principles
Digital optical comparators use optics, camera/imaging, illumination, stage motion, software measurement, and sometimes CAD alignment/pass-fail tools. They are not universal replacements for granite/manual inspection because datum setup, part support, visibility, and criteria still matter.

## Machine-Specific Notes
Public VisionGauge sources describe the 500 Series as a digital optical comparator family with CAD comparison and automated inspection capabilities. They do not prove the shop `QC-1` configuration, travel, fixture, calibration, program, or approved inspection plan.

## Key Process Variables
- Lighting and contrast: affect edge detection.
- Focus and magnification: affect resolution and repeatability.
- Part fixturing/orientation: affects datum alignment.
- CAD/program quality: affects nominal comparison.
- Calibration and stage accuracy: affect measurement trust.
- Surface finish and transparency: affect image quality.

## Process Window Concepts
Optical inspection may be the better alternative when measuring profiles, edge geometry, small visual features, or CAD-comparison characteristics. Granite may be better for physical datum-plane height or flatness checks. The method should follow the inspection characteristic.

## Materials, Parts, Geometry, And Environment Interactions
Flash, translucent material, shadows, curved surfaces, and burrs can confuse optical edges. Soft parts avoid contact deformation under optical methods, but still need stable fixturing.

## Common Failure Modes
- Poor edge detection due to lighting, contrast, burrs, flash, or surface condition.
- Incorrect CAD alignment or program selection.
- Fixture drift or part orientation error.
- Calibration/program not matching current characteristic.
- Overconfidence in auto pass/fail without controlling criteria.

## Failure Mechanisms
Optical measurement error arises when the image edge does not represent the intended functional edge, or when alignment/calibration does not match the datum scheme. Software can repeat the wrong measurement very consistently if the setup is wrong.

## Practical Heuristics
Use optical inspection for visible profile/edge/CAD comparison. Use granite/manual inspection for datum-plane or contact-gauge checks. When the question is "better alternative," ask whether the characteristic is geometric/profile-based, height/flatness-based, visual condition, or acceptance-critical.

## Troubleshooting Logic
Compare the optical result to the granite/manual result only after confirming both use the same datum and characteristic. If they disagree, inspect fixture, lighting, edge definition, calibration, and part support before assuming a part or machine changed.

## Important Terminology
- Optical comparator: inspection system comparing projected/digital part image to expected geometry.
- CAD alignment: software alignment of measured image to CAD nominal.
- Edge detection: software/human identification of feature boundaries.
- Auto pass/fail: software decision logic that still requires approved criteria.

## What This Package Can Help With
It supports bounded recommendations on whether VisionGauge/optical inspection is a better alternative for a given characteristic.

## What This Package Cannot Prove
It cannot prove calibration, program approval, shop criteria, pass/fail status, or that VisionGauge should replace an existing method.

## Source Map
Technical Source Confidence: medium. Strongest support is OEM public product-family information; missing support is shop-specific inspection program and configuration. See `source-map.md`.
