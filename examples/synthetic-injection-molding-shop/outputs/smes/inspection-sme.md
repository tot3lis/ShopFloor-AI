# Inspection SME

## SME Identity

- SME Name: Inspection SME
- SME Type: Inspection coordinator
- Status: Required
- Confidence: High
- Current Source Depth: Level 3
- Source Basis: `shop-reference.md`
- Profile File: `smes/inspection-sme.md`
- Related Shop Reference Sections: Quality Gates; Operation Step Summaries; Machine / Equipment Dictionary

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

- `PL-HOUSING-44` `060 Inspect` is a first article and hourly inspection quality gate.
- `060 Inspect` uses `QC-1` / Vision Gauge 500 and `QC-2` / Granite Surface Plate depending on inspection characteristic.
- `EL-SEAL-12` `065 Check` is a visual and dimensional inspection quality gate.
- `065 Check` primarily uses `QC-2` / Granite Surface Plate, with `QC-1` / Vision Gauge 500 when optical dimensional checks are required.
- `095 MRB Hold` is a conditional MRB/disposition gate outside standard flow.

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

`Inspection SME`, `060 Inspect`, `065 Check`, `095 MRB Hold`, `QC-1`, Vision Gauge 500, `QC-2`, Granite Surface Plate, first article, hourly checks, visual inspection, dimensional inspection.

### Semantic / Plain-Language Triggers

inspection, check, quality gate, acceptance, reject, MRB, disposition, gauge, measured feature, dimensional result, first piece, hourly sample.

### Routing Notes

Invoke with Vision Gauge 500 SME or Granite Surface Plate SME when a question names equipment or asks about measurement method. Invoke with Shop Flow SME when route status or MRB flow matters.

## Questions This SME Can Help Answer Now

- Which operations are inspection or quality gates.
- Which inspection equipment is associated with `060 Inspect` or `065 Check`.
- Whether MRB is standard or conditional.
- Which SME should be asked for optical or manual dimensional inspection context.

## Questions This SME Cannot Answer Yet

- Whether a part passes or fails.
- The controlling acceptance criteria.
- Calibration status, measurement uncertainty, or exact inspection method.
- Root cause or corrective action from inspection results.

## Records This SME Would Ask For

First article records, hourly inspection records, dimensional results, inspection plans, gauge logs, MRB records, and acceptance criteria.

## Documents That Would Level This SME Up

Inspection plan, sampling plan, customer acceptance criteria, gauge instructions, visual standards, and MRB procedure.

## Evidence That Would Level This SME Up

Actual inspection results, gauge records, MRB records, photos, dimensional reports, and signed acceptance records.

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

- None blocking. Detailed acceptance criteria and inspection plans are not yet provided.
