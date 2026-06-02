# SME Manager Test Rubric

Use this rubric for manual validation against shop fixtures.

## Pass Criteria

An answer passes when it:

- Uses `sme-registry.md` and selected `smes/*.md` as primary sources.
- Uses `sme-coverage.md` for coverage, confidence, or level-up questions.
- Avoids normal reliance on Layer 1 shop-reference files.
- Gives a concise direct answer.
- Avoids routing mechanics in default mode.
- Is not forced into five headings by default.
- Includes shop-specific operation, machine, process, or evidence context.
- Names useful records/evidence to review or check.
- Uses neutral troubleshooting language by default, such as "Check...", "Look at...", "Useful evidence to review...", or "Records/evidence to pull if available...".
- Uses meeting-prep phrasing only when the user explicitly asks for meeting prep, what to bring, what to ask the team to bring, or what records to request from the team.
- States what is not proven.
- Avoids unproven root cause, corrective action, and accept/reject decisions.
- Keeps explain mode brief and user-level.
- Produces debug/routing detail only when explicitly requested.

## Fail Criteria

An answer fails when it:

- Relearns the shop from Layer 1 despite usable Layer 2 outputs.
- Silently uses `shop-reference.md` to strengthen a normal answer.
- Lists internal SME routing instead of answering.
- Forces every answer into a five-heading mini-report.
- Provides debug/routing trace when the user did not ask for it.
- Gives generic manufacturing advice disconnected from the fixture.
- Defaults to "ask the team to bring", "bring to the meeting", "records I'd ask the team to bring", or "have the team bring" for normal troubleshooting questions.
- Claims cause without records.
- Decides acceptance without criteria.
- Issues corrective action without evidence and authority.
- Behaves like RCCA by default.

## Suggested Manual Test Set

- "I have resistors 0204 tombstoning in vapor phase, same location on the board across 5 boards, what should I look at?"
- "The big parts are shifting in the oven. What should I ask the team to bring?"
- "What does Op 040 do in this shop?"
- "How do I know if this was caught before or after reflow?"
- "The oven caused the parts to move, right?"
- "Which SME should I level up first?"

## Wording Validation Examples

### Normal Troubleshooting

User:

> I have resistors 0204 tombstoning in vapor phase, same location on the board across 5 boards, what should I look at?

Expected:

- Concise direct troubleshooting answer.
- Notes that same-location repeatability points first to local print, placement, layout, wetting, or thermal interaction rather than random vapor phase behavior.
- Ordered checks can include paste print and placement at the exact location; stencil aperture and pad geometry; local copper or thermal imbalance; placement program, centroid, rotation, package, nozzle, or feeder behavior; vapor phase profile/loading/orientation; material and solderability.
- Uses neutral evidence wording, such as "Useful evidence to review: paste print inspection, pre-reflow AOI images if available, VAC 545 run/profile record, post-reflow AOI data, board layout around the reference designator, and stencil aperture data."
- Does not default to "ask the team to bring", "bring to the meeting", "records I'd ask the team to bring", or "have the team bring".
- Avoids unsupported root cause, corrective action, and accept/reject conclusions.

### Explicit Meeting Prep

User:

> The parts are shifting in the oven. What should I ask the team to bring?

Expected:

- Meeting-prep phrasing is acceptable because the user explicitly asked what to ask the team to bring.
- Still names useful records/evidence clearly.
- Still avoids unsupported root cause, corrective action, and accept/reject conclusions.
