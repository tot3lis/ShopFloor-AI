# Arburg Allrounder 470 SME

## SME Identity

- SME Name: Arburg Allrounder 470 SME
- SME Type: Machine / Capability
- Status: Required
- Confidence: High
- Current Source Depth: Level 3
- Source Basis: `shop-reference.md`
- Profile File: `smes/arburg-allrounder-470-sme.md`
- Related Shop Reference Sections: Operation Step Summaries; Machine / Equipment Dictionary; Route-To-SME Mapping

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

- Machine/capability name: `IM-110` / Arburg Allrounder 470.
- Type: Injection Molding Press.
- Related operation: `040 Mold Parts`.
- Related work center: `5200`.
- Standard route status: primary press for `PL-HOUSING-44`.
- Supported capability: injection molding of thermoplastic housing parts.
- Related tooling: mold `MX-44A` appears in setup/molding context.

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

`IM-110`, Arburg Allrounder 470, Arburg, `040 Mold Parts`, `5200`, `PL-HOUSING-44`, primary press.

### Semantic / Plain-Language Triggers

housing press, injection molding press, molded housing, primary molding machine, press selection, molding run context.

### Routing Notes

Invoke with Shop Flow SME for route sequence and with MX-44A Mold SME for mold/tooling context. Invoke with Nissei FNX180 SME when comparing primary and backup presses.

## Questions This SME Can Help Answer Now

- Whether `IM-110` is the primary press for `PL-HOUSING-44`.
- Which operation and work center the press supports.
- Which related SMEs may be needed for housing molding context.

## Questions This SME Cannot Answer Yet

- Specific molding parameters, programs, alarms, maintenance state, or actual run history.
- Whether `IM-110` caused a defect.
- Whether a part was acceptable after molding.

## Records This SME Would Ask For

Press setup sheet, molding run record, machine log, material configuration, traveler, and inspection results.

## Documents That Would Level This SME Up

Press manual, setup instructions, process parameters, tooling setup sheet, material processing specification.

## Evidence That Would Level This SME Up

Actual cycle records, alarm logs, setup records, process monitoring data, maintenance records, and molded-part inspection results.

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
