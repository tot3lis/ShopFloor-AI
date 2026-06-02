# Shop Flow SME

## SME Identity

- SME Name: Shop Flow SME
- SME Type: Shop flow
- Status: Required
- Confidence: High
- Current Source Depth: Level 3
- Source Basis: `shop-reference.md`
- Profile File: `smes/shop-flow-sme.md`
- Related Shop Reference Sections: Standard Operation Flow; Operation Dictionary; Operation Step Summaries; Work Center Dictionary; Shop-Specific Language

## Required Disclaimer

This is a shell generated from shop-reference.md, not a full technical SME knowledge pack.

## What This SME Knows Now

- The shop has two product flows: `PL-HOUSING-44` / `RTR-PL-884` and `EL-SEAL-12` / `RTR-EL-201`.
- `PL-HOUSING-44` flows through `010 Issue Resin`, `020 Dry Material`, `030 Setup Mold`, `040 Mold Parts`, `050 Trim/Gate`, `060 Inspect`, and `070 Pack`.
- `EL-SEAL-12` flows through `010 Issue Material`, `025 Prep Compound`, `035 Compression Mold`, `045 Post Cure`, `055 Deflash`, `065 Check`, and `075 Pack/Label`.
- `095 MRB Hold` is conditional MRB/disposition and is excluded from standard flow.
- Work center relationships include material issue `5100`, drying `5110`, post cure `5120`, injection molding `5200`, compression molding `5210`, trim/deflash `5300`, inspection `5400`, packaging `5500`, MRB `9999`, and `Unknown` for `025 Prep Compound`.
- Known machine-to-operation mappings are listed in `shop-reference.md`.

## When To Route Questions To This SME

Routing triggers are semantic hints, not strict exact-match rules.

### Exact / Named Triggers

`Shop Flow SME`, `PL-HOUSING-44`, `RTR-PL-884`, `EL-SEAL-12`, `RTR-EL-201`, `010 Issue Resin`, `020 Dry Material`, `030 Setup Mold`, `040 Mold Parts`, `050 Trim/Gate`, `060 Inspect`, `070 Pack`, `095 MRB Hold`, `025 Prep Compound`, `035 Compression Mold`, `045 Post Cure`, `055 Deflash`, `065 Check`, `075 Pack/Label`.

### Semantic / Plain-Language Triggers

route sequence, standard flow, operation order, what happens before or after, conditional operation, MRB routing, work center meaning, product flow, machine handoff, material-dependent route.

### Routing Notes

Invoke this SME with any machine SME when the question depends on upstream/downstream context, route status, or whether an operation is standard, conditional, optional, or skipped.

## Questions This SME Can Help Answer Now

- Which operation comes before or after another operation.
- Whether `095 MRB Hold` is part of standard flow.
- Which product flow contains a named operation.
- Which work center is associated with a route operation.
- Which machine SMEs are relevant to a route step.

## Questions This SME Cannot Answer Yet

- Whether a specific unit actually completed an operation.
- Exact cycle times, recipes, acceptance criteria, or setup parameters.
- Root cause, corrective action, or defect disposition.
- Detailed procedure requirements not present in `shop-reference.md`.

## Records This SME Would Ask For

Traveler, work order, router revision, operation completion records, material configuration, MRB record, and actual build history.

## Documents That Would Level This SME Up

Router control procedure, work order examples, traveler examples, MRB procedure, work center definitions, and routing change procedure.

## Evidence That Would Level This SME Up

Completed travelers, operation timestamps, actual routing records, MRB transactions, and product-specific build records.

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

- Is `UNKNOWN-7` Old Conair Dryer retired, retained as backup, or irrelevant to this shop flow?
- When `CRYO-1` is restored, should it become normal for high-volume `EL-SEAL-12` deflash or remain optional?
