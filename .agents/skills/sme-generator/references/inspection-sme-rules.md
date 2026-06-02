# Inspection SME Rules

Always generate `Inspection SME`.

Inspection SME is a shop-level coordinator for inspection, test handoffs, acceptance-document needs, and evidence questions found in `shop-reference.md`.

## Purpose

Inspection SME covers:

- inspection points in `shop-reference.md`
- visual/manual inspection
- AOI
- CMM, NDI, measurement, dimensional checks
- final inspection and final acceptance
- test-related inspection handoffs
- acceptance documents, criteria, specs, drawings, photos, or records that would improve the shell

## Router Trigger Guidance

Exact / Named Triggers should include:

- `Inspection SME`
- inspection operation numbers
- inspection operation names
- inspection work centers
- named inspection/test machines
- named inspection/test records
- named acceptance documents if present

Semantic / Plain-Language Triggers should include:

- inspection
- check
- verify
- acceptance
- criteria
- defect confirmation
- evidence
- photo
- AOI
- CMM
- visual inspection
- final inspection
- test result
- accept/reject
- workmanship
- drawing
- spec
- before or after
- was it caught
- how do we know
- what proof do we need

## Named Inspection Machines

If there is a named inspection machine or station, create both:

- `Inspection SME`
- a Machine / Capability SME for the named machine or station

Examples:

- `Inspection SME`
- `Koh Young Zenith SME`
- `Zeiss Contura G2 SME`
- `Visual Inspection Bench SME`

## Status

Inspection SME is Required by default.

If the source only says generic `Inspect`, `Check`, or `Verify`, keep the Inspection SME but lower confidence and create open questions about what inspection means.

## Boundaries

- Cannot make final accept/reject decisions without controlling acceptance criteria.
- Cannot infer defect cause.
- Cannot replace workmanship, specification, customer, or drawing requirements.
- Should not overclaim when the source only says generic inspection language.
