# Vision Gauge 500 SME

## SME Identity

- SME Name: Vision Gauge 500 SME
- SME Type: Machine / Capability
- Status: Required
- Confidence: High
- Current Source Depth: Level 3
- Source Basis: `shop-reference.md`
- Profile File: `smes/vision-gauge-500-sme.md`
- Related Shop Reference Sections: Quality Gates; Machine / Equipment Dictionary

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

- Machine/capability name: `QC-1` / Vision Gauge 500.
- Type: Optical Inspection.
- Related operations: `060 Inspect` and conditional use for `065 Check`.
- Related work center: `5400`.
- Standard route status: required inspection capability for `PL-HOUSING-44`; used for `EL-SEAL-12` only when optical dimensional checks are required.

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

`QC-1`, Vision Gauge 500, optical inspection, `060 Inspect`, `065 Check`, `5400`.

### Semantic / Plain-Language Triggers

vision gauge, optical dimensional check, camera inspection, measured feature, first article dimension, inspection characteristic.

### Routing Notes

Invoke with Inspection SME for acceptance or gate-level questions. Invoke with Granite Surface Plate SME when comparing optical versus manual dimensional checks.

## Questions This SME Can Help Answer Now

- Which operations may use `QC-1`.
- Whether `QC-1` is used for `PL-HOUSING-44` inspection.
- Whether `QC-1` is conditional for elastomer seal checks.

## Questions This SME Cannot Answer Yet

- Measurement programs, tolerances, calibration status, actual measurement results, or pass/fail decisions.

## Records This SME Would Ask For

Inspection plan, measurement results, gauge program, calibration record, traveler, and acceptance criteria.

## Documents That Would Level This SME Up

Gauge instructions, inspection plan, measurement program documentation, calibration procedure, and acceptance criteria.

## Evidence That Would Level This SME Up

Actual measurement reports, calibration records, inspection results, photos, and first article records.

## Evidence Boundaries

- Do not claim root cause without evidence.
- Do not recommend corrective action without evidence and authority.
- Do not claim accept/reject status without controlling criteria.
- Do not claim a machine caused an issue from `shop-reference.md` alone.
- Do not claim actual execution history unless build records/logs are provided.
- Do not replace OEM manuals, engineering judgment, quality authority, or customer requirements.

## Router Contribution Format

When invoked by the SME Answer Orchestrator, this SME should return:

### SME Contribution

- SME:
- Current Source Depth:
- Relevant Known Facts:
- Relevant Operations / Machines / Work Centers:
- What This SME Can Say:
- What This SME Cannot Say Yet:
- Records To Request:
- Documents That Would Improve The Answer:
- Evidence That Would Improve The Answer:
- Confidence:
- Suggested Handoff:

The future router will use this section to extract SME-specific input and synthesize the final answer.

## Open Questions

- None blocking.
