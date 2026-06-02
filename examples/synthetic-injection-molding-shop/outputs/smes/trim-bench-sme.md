# Trim Bench SME

## SME Identity

- SME Name: Trim Bench SME
- SME Type: Machine / Capability
- Status: Required
- Confidence: High
- Current Source Depth: Level 3
- Source Basis: `shop-reference.md`
- Profile File: `smes/trim-bench-sme.md`
- Related Shop Reference Sections: Operation Step Summaries; Machine / Equipment Dictionary

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

- Machine/capability name: `BENCH-TRIM` / Trim Bench.
- Type: Manual Bench.
- Related operations: `050 Trim/Gate` and `055 Deflash`.
- Related work center: `5300`.
- Standard route status: required for manual trim/gate removal and current normal hand deflash.
- Related product flows: `PL-HOUSING-44` and `EL-SEAL-12`.

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

`BENCH-TRIM`, Trim Bench, `050 Trim/Gate`, `055 Deflash`, `5300`, hand deflash, manual trim.

### Semantic / Plain-Language Triggers

trim bench, gate removal, hand trim, hand deflash, manual finishing, remove flash, remove gates.

### Routing Notes

Invoke with Arrow Cryogenic Deflasher SME when the question compares hand deflash to cryogenic deflash. Invoke with Inspection SME when trim or deflash quality is being evaluated.

## Questions This SME Can Help Answer Now

- Which bench supports `050 Trim/Gate`.
- Which current normal method supports `055 Deflash`.
- Which product flows use manual finishing.

## Questions This SME Cannot Answer Yet

- Detailed trim criteria, workmanship standard, tool list, ergonomic method, or accept/reject decision.

## Records This SME Would Ask For

Traveler, trim/deflash instruction, inspection results, visual standard, and operator signoff if available.

## Documents That Would Level This SME Up

Trim instruction, deflash instruction, workmanship criteria, visual standards, and tool list.

## Evidence That Would Level This SME Up

Actual trim records, photos, inspection records, nonconformance records, and operator signoffs.

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
