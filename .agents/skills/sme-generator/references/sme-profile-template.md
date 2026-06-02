# {SME Name}

## SME Identity

- SME Name:
- SME Type:
- Status:
- Confidence:
- Current Source Depth:
- Source Basis:
- Profile File:
- Related Shop Reference Sections:

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

List only facts supported by `shop-reference.md`.

For Machine / Capability SMEs, include:

- machine/capability name
- known aliases or alternate names
- related operation numbers
- related operation names
- related work centers
- standard route status
- supported process/capability
- related inspection/test handoffs if present
- likely records associated with this machine/capability

For Shop Flow SME, include:

- known standard operation flow
- upstream/downstream relationships
- operation sequence
- work center relationships
- known machine-to-operation mappings
- unresolved flow questions

For Inspection SME, include:

- known inspection points
- known inspection machines/capabilities
- known test/inspection handoffs
- known acceptance-document needs
- unresolved inspection/acceptance questions

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

Include exact shop-specific identifiers such as SME name, machine name, operation numbers, operation names, work centers, named records, named documents, and named capabilities.

### Semantic / Plain-Language Triggers

Include plain-language concepts that could imply this SME, even if the user does not use exact shop terminology.

### Routing Notes

Include when the future router should invoke this SME alongside Shop Flow SME, Inspection SME, upstream/downstream machine SMEs, or related capability SMEs.

## Questions This SME Can Help Answer Now

List practical question types answerable from the current shell and `shop-reference.md`.

## Questions This SME Cannot Answer Yet

List questions that require Level 4 documents or Level 5 evidence.

## Records This SME Would Ask For

List records this SME would request when invoked. Do not claim records exist unless `shop-reference.md` says they exist.

## Documents That Would Level This SME Up

List documents that would move the SME from Level 3 to Level 4.

## Evidence That Would Level This SME Up

List evidence that would move the SME from Level 4 to Level 5.

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

List unresolved mapping or confidence questions from `shop-reference.md`.
