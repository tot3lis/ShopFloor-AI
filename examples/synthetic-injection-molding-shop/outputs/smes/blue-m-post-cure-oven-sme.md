# Blue M Post Cure Oven SME

## SME Identity

- SME Name: Blue M Post Cure Oven SME
- SME Type: Machine / Capability
- Status: Required
- Confidence: High
- Current Source Depth: Level 3
- Source Basis: `shop-reference.md`
- Profile File: `smes/blue-m-post-cure-oven-sme.md`
- Related Shop Reference Sections: Operation Step Summaries; Machine / Equipment Dictionary

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

- Machine/capability name: `OV-9` / Blue M Post Cure Oven.
- Type: Oven.
- Related operation: `045 Post Cure`.
- Related work center: `5120`.
- Standard route status: required for `EL-SEAL-12` silicone/elastomer post cure.

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

`OV-9`, Blue M Post Cure Oven, Blue M, `045 Post Cure`, `5120`, `EL-SEAL-12`.

### Semantic / Plain-Language Triggers

post cure, oven cure, silicone cure, elastomer cure, cure oven, heat cure.

### Routing Notes

Invoke with Shop Flow SME for upstream compression molding and downstream deflash/inspection context.

## Questions This SME Can Help Answer Now

- Which oven supports `045 Post Cure`.
- Which product flow uses the post cure oven.
- Which route steps surround post cure.

## Questions This SME Cannot Answer Yet

- Cure time, temperature, oven profile, actual cure completion, or acceptability.

## Records This SME Would Ask For

Cure log, oven run record, traveler, material lot, work order, and post-cure inspection records.

## Documents That Would Level This SME Up

Oven manual, cure recipe/specification, silicone processing instruction, and post-cure work instruction.

## Evidence That Would Level This SME Up

Actual oven logs, cure records, temperature charts, traveler signoffs, and inspection results.

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
