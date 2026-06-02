# Knowledge Package: Packaging And Labeling

## Package Purpose
This package gives packaging/labeling SMEs practical technical context for industrial thermal label printing and label quality.

## Applies To
Zebra ZT411 Label Printer SME, Shop Flow SME, Inspection SME as downstream verification context.

## Knowledge Level
Process-subtype knowledge.

- Input Mapping Confidence: high
- Technical Source Confidence: medium
- Source tier coverage: generated SME shell, Zebra OEM sources, public thermal-transfer guidance

## Process Overview
Industrial labeling converts product/order information into printed labels that must remain legible, scannable, and correct for the required use. In this shop, `PKG-1 Zebra ZT411 Label Printer` supports `PL-HOUSING-44` `070 Pack` and `EL-SEAL-12` `075 Pack`.

## Core Principles
Thermal label quality depends on print technology, media, ribbon, printhead heat/darkness, speed, pressure, resolution, label design, barcode requirements, and printer condition. Direct thermal uses heat-sensitive media; thermal transfer uses ribbon melted onto label substrate.

## Equipment / Tooling / System Principles
The printer feeds media, applies heat through a printhead, controls speed/darkness, senses label position, and may use ribbon depending on mode. Media/ribbon compatibility and printhead condition are central to consistent print quality.

## Machine-Specific Notes
Public Zebra sources support ZT411 as an industrial 4-inch printer with thermal transfer/direct thermal capability and multiple resolution options. They do not prove the shop's installed resolution, media, ribbon, network setup, templates, or approved label content.

## Key Process Variables
Print speed, darkness/heat, printhead pressure, ribbon-media match, label stock, resolution, barcode size, media sensor setup, printhead cleanliness, and template correctness.

## Process Window Concepts
Label printing has a quality window: enough heat/pressure for readable marks without smearing, burn-through, ribbon wrinkle, barcode growth, or printhead wear. Faster speeds can reduce available heat transfer, especially with certain media/ribbon combinations.

## Materials, Parts, Geometry, And Environment Interactions
Label substrate, adhesive, ribbon chemistry, product environment, handling, moisture, abrasion, and scan distance affect label durability and readability.

## Common Failure Modes
Faded print, overly dark print, barcode growth, unreadable barcode, ribbon wrinkle, media drift, poor adhesion, wrong label template, sensor errors, and printhead streaks.

## Failure Mechanisms
Heat/speed/pressure/media mismatch changes mark formation. Dirty or worn printheads create missing lines. Wrong ribbon or media can smear, fade, or fail durability needs. Incorrect templates can print correct-looking but wrong information.

## Practical Heuristics
For quality questions, separate content correctness from print quality. For print quality, check media/ribbon match, speed/darkness, pressure, cleanliness, and printer calibration. For acceptance, rely on customer/shop label requirements.

## Troubleshooting Logic
Compare whether issues follow the printer, media/ribbon lot, template/file, label size, or operator setup. Avoid assuming printer hardware fault before consumables and setup are checked.

## Important Terminology
- Direct thermal: heat-sensitive media darkens without ribbon.
- Thermal transfer: heated printhead transfers ribbon material to label.
- Darkness: heat/energy setting.
- Barcode grade: quality/readability measure under a defined standard.

## What This Package Can Help With
It supports SME answers about labeling process variables and common print-quality mechanisms.

## What This Package Cannot Prove
It cannot prove customer label requirements, approved templates, barcode acceptance, root cause, or corrective action.

## Source Map
Technical Source Confidence: medium. See `source-map.md`.
