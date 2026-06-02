# Knowledge Package: Zebra ZT411 Printer Model

## Package Purpose
This package gives the Zebra ZT411 Label Printer SME public model-specific context for `PKG-1`.

## Applies To
Zebra ZT411 Label Printer SME and Packaging And Labeling package.

## Knowledge Level
Machine/model-specific public knowledge.

- Input Mapping Confidence: high
- Technical Source Confidence: high
- Source tier coverage: generated SME shell, Zebra OEM product/specification sources

## Process Overview
The Zebra ZT411 is an industrial 4-inch label printer model that supports thermal transfer and direct thermal printing. Public Zebra sources identify configurable resolutions and connectivity/media-handling options.

## Core Principles
Model capability defines what the printer can generally do; shop configuration defines what it is actually set up to do. The ZT411 can support durable industrial labels when media, ribbon, settings, template, and verification are controlled.

## Equipment / Tooling / System Principles
The printer uses a thermal printhead, platen roller, media path, sensors, ribbon path if thermal transfer is used, firmware/settings, and connectivity/software interface. Quality depends on mechanical setup and print parameters.

## Machine-Specific Notes
Shop-specific fact: `PKG-1 Zebra ZT411 Label Printer` supports packing operations. Public model facts do not prove the shop's resolution, firmware, media handling option, print mode, or label template.

## Key Process Variables
Resolution, print width, speed, darkness, media/ribbon selection, printhead pressure, sensor calibration, template/barcode design, and printer cleanliness.

## Process Window Concepts
Model specs set possible capability boundaries, but print quality depends on selected mode and consumables. High speed can trade against darkness/readability depending on media/ribbon.

## Materials, Parts, Geometry, And Environment Interactions
Label durability depends on substrate, ribbon chemistry, adhesive, surface, abrasion, heat, chemicals, and expected label life.

## Common Failure Modes
Faded print, missing lines, barcode scan failures, ribbon wrinkle, media drift, poor adhesion, and wrong template/file selection.

## Failure Mechanisms
Printhead heat transfers marks to media or ribbon. Mechanical pressure, media movement, and sensing determine registration. Bad consumable match or dirty/worn printhead degrades image formation.

## Practical Heuristics
Use public ZT411 data for capability context only. Use shop label specifications and actual printer configuration for acceptance or troubleshooting decisions.

## Troubleshooting Logic
Separate printer model capability from actual configured state. Verify whether the issue follows settings, media/ribbon, printhead, template, or network/software path.

## Important Terminology
- DPI: dots per inch resolution.
- IPS: inches per second print speed.
- Thermal transfer: ribbon-based print method.
- Direct thermal: heat-sensitive media print method.

## What This Package Can Help With
It supports accurate model-aware explanations for `PKG-1`.

## What This Package Cannot Prove
It cannot prove shop setup, approved templates, label correctness, barcode acceptability, or printer condition.

## Source Map
Technical Source Confidence: high for public model context. See `source-map.md`.
