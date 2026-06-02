# Matsui Dryer 1 SME

## SME Identity

- SME Name: Matsui Dryer 1 SME
- SME Type: Machine / Capability
- Status: Required
- Confidence: High
- Current Source Depth: Level 3
- Source Basis: `shop-reference.md`
- Profile File: `smes/matsui-dryer-1-sme.md`
- Related Shop Reference Sections: Operation Step Summaries; Machine / Equipment Dictionary

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

- Machine/capability name: `DRY-1` / Matsui Dryer 1.
- Type: Resin Dryer.
- Related operation: `020 Dry Material`.
- Related work center: `5110`.
- Standard route status: required material-dependent candidate for nylon resin used by `PL-HOUSING-44`.

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

`DRY-1`, Matsui Dryer 1, Matsui, nylon, `020 Dry Material`, `5110`, `PL-HOUSING-44`.

### Semantic / Plain-Language Triggers

nylon drying, resin dryer, material drying, moisture conditioning, dryer for housing material.

### Routing Notes

Invoke with Dri-Air Dryer 2 SME for material-dependent dryer comparisons and Shop Flow SME for route context.

## Questions This SME Can Help Answer Now

- Which dryer is associated with nylon resin for `PL-HOUSING-44`.
- Which operation and work center include resin drying.

## Questions This SME Cannot Answer Yet

- Drying temperature, time, dew point, actual drying completion, or material acceptability.

## Records This SME Would Ask For

Dryer log, material lot, material configuration, work order, drying recipe, and moisture/condition evidence if available.

## Documents That Would Level This SME Up

Dryer manual, nylon drying specification, material handling procedure, and drying work instruction.

## Evidence That Would Level This SME Up

Actual dryer records, material lot records, time/temperature logs, moisture readings, and traveler signoffs.

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
