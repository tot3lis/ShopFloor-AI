# ShopContext Output Template

Use this file to choose the response shape.

## Output Length Control

ShopContext should avoid producing oversized duplicate outputs.

For simulated validation or setup review, do not output both:

- a full ShopContext Review, and
- a full draft `shop-reference.md`

unless the user explicitly requests the full draft reference.

Default setup/validation responses should be compact and include:

1. Validation verdict or setup summary
2. Key extracted flow summary
3. Major operation-instruction, machine, work-center, or quality-gate uncertainties
4. Open user questions for review-stage use
5. Required reference/test patches, if any
6. Optional improvements, if any
7. Ready/not-ready decision

Avoid duplicating the same operation, work center, machine mapping, instruction summary, and quality-gate tables across multiple sections.

The official final output file name is `shop-reference.md`.

Treat `reference.md` as an informal user alias for `shop-reference.md`. If a user asks for `reference.md`, treat it as a request for `shop-reference.md` unless they explicitly require the exact filename `reference.md`.

Do not create both `reference.md` and `shop-reference.md`.

If the user asks for the final reference file and blocking open questions remain, do not output final `shop-reference.md`, `reference.md`, or any other final reference file. Output `ShopContext Review - User Confirmation Needed` instead.

A request to `generate reference.md`, `generate shop-reference.md`, `create the reference`, `write the reference`, or `save the reference` does not override the Blocking Review Gate.

If no blocking open questions exist, output the complete lean `shop-reference.md` directly.

If the user asks for validation only, output the compact validation format.

If the user asks for both validation and full reference, output both only when no blocking open questions exist. If blocking open questions exist, output only `ShopContext Review - User Confirmation Needed`.

# ShopContext Setup Review

Use User Setup Mode when the user uploads or provides shop setup inputs such as routers, work orders, travelers, operation lists, work centers, machine lists, asset exports, operation instructions, or user notes.

User Setup Mode is the default for real shop setup.

In User Setup Mode, do not output the full `shop-reference.md`.

Only generate the full `shop-reference.md` when the user explicitly asks for the full, final, complete, draft, or generated reference file and no blocking open questions remain.

## 1. What I Found

Short plain-language summary of the shop flow and major inputs found.

Keep this to 5-8 bullets maximum.

## 2. What I'm Unsure About

List only the major uncertain mappings, vague operations, missing instruction links, or unresolved equipment/work-center relationships.

Keep this to the highest-impact issues only.

## 3. Questions For You

Ask only the questions needed to improve the shop reference.

Prefer 5-10 targeted questions.

Do not ask the user to re-explain the whole shop.

## 4. Next Step

Tell the user to reply with answers/corrections.

State that the full `shop-reference.md` will only be generated when requested.

# Full ShopContext Review

Use this format when the user asks for a detailed review before finalization:

## 1. Sources Reviewed

List the routers, work orders, travelers, operation lists, machine lists, operation instructions, asset exports, and user notes reviewed.

## 2. Extracted Operation Flow

Show the operation sequence extracted from the source documents. Preserve operation numbers exactly.

## 3. Operation Dictionary

List each operation number, operation name, work center, plain-English meaning, product or route usage, and notes.

## 4. Operation Instruction Summaries

Summarize attached instructions into internal process steps. Do not copy full instructions.

Flag vague operations with missing or unmatched instructions.

## 5. Work Center Dictionary

List each work center and the work it appears to perform.

## 6. Machine / Equipment Dictionary

List machines, equipment, fixtures, benches, stations, lines, cells, and tools. Preserve names and asset IDs exactly.

## 7. Proposed Operation-To-Machine / Equipment Mapping

Use the mapping table from `operation-machine-mapping-rules.md` during review.

## 8. Quality Gates

List operations or internal steps where defects may be detected, accepted, reviewed, tested, verified, or dispositioned.

## 9. Low-Confidence Or Unmapped Items

List low-confidence mappings, unknown mappings, missing operation instructions, unmapped machines/equipment, and unresolved contradictions.

## 10. Questions For User Review

Ask specific targeted questions tied to exact operations, instructions, work centers, machines, or source documents.

## 11. Draft shop-reference.md

Provide the draft reference file content using the required lean `shop-reference.md` structure only when the user explicitly asks for a full draft reference and blocking open questions do not exist.

If blocking open questions exist, omit this section and output only `ShopContext Review - User Confirmation Needed`.

# ShopContext Simulated Validation

## 1. Verdict

Ready / Not Ready / Needs Patch

## 2. What Passed

Short bullets only.

## 3. What Looked Weak

Short bullets only.

## 4. Required Patches

Only list blocking changes.

## 5. Optional Improvements

List non-blocking refinements.

## 6. Ready For First Real-Use Testing?

Yes / No, with a short explanation.

# Final Output Format

When the user approves or asks for the final file, provide:

```md
# Shop Reference

## 1. Shop Type / Process Context

## 2. Standard Operation Flow

## 3. Operation Dictionary

## 4. Operation Step Summaries

## 5. Work Center Dictionary

## 6. Machine / Equipment Dictionary

## 7. Quality Gates

## 8. Shop-Specific Language
```

If non-blocking uncertainty remains after review, preserve it briefly in the relevant final section using clear language such as `Unknown`, `appears to`, or `likely`.

Do not include a final open-questions section.

Do not include unresolved blocking questions, blocking uncertainty, unresolved blocking mappings, or review questions inside final `shop-reference.md` or any explicitly required final `reference.md`. Preserving blocking uncertainty or questions inside a final reference file is a gate failure.

Do not include generic evidence-source or likely-records sections. Include records/logs only when the source explicitly confirms they are retained or used, and place them inside the relevant Operation Step Summary as `Confirmed Records / Logs`.

Low confidence does not stop drafting. Low confidence does stop finalization. Drafts may contain clearly labeled uncertainty; final output requires user confirmation or correction of blocking uncertain items.

Do not create, write, save, or present final `shop-reference.md`, final `reference.md`, or any final reference file while blocking open questions remain unanswered.

A final `shop-reference.md` is only allowed after blocking open questions are answered, or after ShopContext determines there are no blocking open questions. Use `reference.md` only when the user explicitly requires that exact filename.

If blocking open questions exist, output exactly this review shape:

# ShopContext Review - User Confirmation Needed

## Sources Reviewed

## Draft Findings Summary

## Blocking Open Questions

## Next Step

Tell the user to answer the blocking questions. Do not include final `shop-reference.md`, final `reference.md`, or any final reference file.

If the user does not answer clearly, output:

# ShopContext Review - Still Blocked

List the blocking questions that remain. Do not create final `shop-reference.md`, final `reference.md`, or any final reference file.

If the user explicitly asks to proceed without answering blocking questions, create or present only `shop-reference-draft.md`, or a clearly labeled draft-only reference. Do not create final `shop-reference.md`, final `reference.md`, or any final reference file.
