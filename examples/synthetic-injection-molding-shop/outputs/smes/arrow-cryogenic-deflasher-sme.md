# Arrow Cryogenic Deflasher SME

## SME Identity

- SME Name: Arrow Cryogenic Deflasher SME
- SME Type: Machine / Capability
- Status: Conditional
- Confidence: Medium
- Current Source Depth: Level 3
- Source Basis: `shop-reference.md`
- Profile File: `smes/arrow-cryogenic-deflasher-sme.md`
- Related Shop Reference Sections: Operation Step Summaries; Machine / Equipment Dictionary; Shop-Specific Language

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

- Machine/capability name: `CRYO-1` / Arrow Cryogenic Deflasher.
- Type: Deflash Machine.
- Related operation: `055 Deflash`.
- Related work center: `5300`.
- Route status: conditional/alternate only.
- Current status in `shop-reference.md`: down; not current normal method.
- Current normal deflash uses `BENCH-TRIM` / Trim Bench for hand deflash.

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

`CRYO-1`, Arrow Cryogenic Deflasher, Arrow, `055 Deflash`, `5300`, cryogenic deflash.

### Semantic / Plain-Language Triggers

cryo deflash, alternate deflash, high-volume seal deflash, deflash machine, down deflasher.

### Routing Notes

Invoke with Trim Bench SME when comparing current hand deflash to possible cryogenic deflash. Invoke with Shop Flow SME for route status.

## Questions This SME Can Help Answer Now

- Whether `CRYO-1` is current normal equipment for `055 Deflash`: it is not.
- How it relates to the current trim bench deflash route.
- Why it is conditional in the SME registry.

## Questions This SME Cannot Answer Yet

- Whether `CRYO-1` is repaired, qualified, or suitable for a specific job.
- Deflash parameters or actual equipment performance.

## Records This SME Would Ask For

Equipment status, maintenance record, deflash work order, qualification record, traveler, and inspection results.

## Documents That Would Level This SME Up

Deflasher manual, deflash work instruction, equipment restoration/qualification record, and deflash acceptance criteria.

## Evidence That Would Level This SME Up

Actual machine status records, maintenance records, run logs, job records, and inspection evidence.

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

- When `CRYO-1` is restored, should it become normal for high-volume `EL-SEAL-12` deflash or remain optional?
