# MX-44A Mold SME

## SME Identity

- SME Name: MX-44A Mold SME
- SME Type: Machine / Capability
- Status: Required
- Confidence: High
- Current Source Depth: Level 3
- Source Basis: `shop-reference.md`
- Profile File: `smes/mx-44a-mold-sme.md`
- Related Shop Reference Sections: Operation Dictionary; Operation Step Summaries; Shop-Specific Language

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

- Equipment/tooling name: `MX-44A`.
- Type/capability: mold/tooling named in `030 Setup Mold` for `PL-HOUSING-44`.
- Related operations: `030 Setup Mold` and `040 Mold Parts`.
- Related work center: `5200`.
- Standard route status: required tooling context for thermoplastic housing mold setup and molding.
- Related machines: `IM-110` / Arburg Allrounder 470 and `IM-220` / Nissei FNX180 candidate presses.

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

`MX-44A`, mold `MX-44A`, `030 Setup Mold`, `040 Mold Parts`, `PL-HOUSING-44`, `5200`.

### Semantic / Plain-Language Triggers

housing mold, mold setup, tooling, injection mold, mold used for housing, mold and press pairing.

### Routing Notes

Invoke with Arburg Allrounder 470 SME or Nissei FNX180 SME for press/tooling questions. Invoke with Shop Flow SME for route context.

## Questions This SME Can Help Answer Now

- Which product and operations mention mold `MX-44A`.
- Which route step performs mold setup.
- Which press SMEs are related to the mold context.

## Questions This SME Cannot Answer Yet

- Mold design, cavity count, maintenance history, tooling condition, setup parameters, or actual tool performance.

## Records This SME Would Ask For

Mold setup sheet, tooling maintenance record, press setup record, work order, and molded-part inspection results.

## Documents That Would Level This SME Up

Mold setup instruction, tooling drawing/specification, tooling maintenance procedure, and press-specific setup documentation.

## Evidence That Would Level This SME Up

Actual setup records, tooling maintenance records, press run records, mold condition reports, and inspection results.

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
