# Zebra ZT411 Label Printer SME

## SME Identity

- SME Name: Zebra ZT411 Label Printer SME
- SME Type: Machine / Capability
- Status: Required
- Confidence: High
- Current Source Depth: Level 3
- Source Basis: `shop-reference.md`
- Profile File: `smes/zebra-zt411-label-printer-sme.md`
- Related Shop Reference Sections: Operation Step Summaries; Machine / Equipment Dictionary

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

- Machine/capability name: `LBL-1` / Zebra ZT411 Label Printer.
- Type: Label Printer.
- Related operation: `075 Pack/Label`.
- Related work center: `5500`.
- Standard route status: required for packaging label print in the elastomer seal flow.

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

`LBL-1`, Zebra ZT411 Label Printer, Zebra, `075 Pack/Label`, `5500`, label print.

### Semantic / Plain-Language Triggers

pack label, customer label, printed label, packaging label, label printer, label format.

### Routing Notes

Invoke with Shop Flow SME for packaging route context. Invoke with Inspection SME only when label acceptance or verification is part of the question.

## Questions This SME Can Help Answer Now

- Which label printer is tied to `075 Pack/Label`.
- Which product flow has a named label-print operation.

## Questions This SME Cannot Answer Yet

- Label content requirements, customer label criteria, printer setup, actual printed-label evidence, or label acceptability.

## Records This SME Would Ask For

Label template, print record, packaging instruction, customer requirement, traveler, and label verification record.

## Documents That Would Level This SME Up

Label printer manual, label template procedure, packaging instruction, and customer labeling requirements.

## Evidence That Would Level This SME Up

Actual print logs, label scans, packaging records, label verification records, and customer acceptance evidence.

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
