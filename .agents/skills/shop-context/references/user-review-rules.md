# User Review Rules

Open questions should help the user correct or confirm only the parts that matter. Do not ask the user to re-explain everything.

## When To Ask Questions

Create open questions for:

- Unmapped operations
- Unmapped machines
- Low-confidence mappings
- Unknown-confidence mappings
- Contradictory source information
- Important missing work centers
- Missing, ambiguous, or unmatched attached operation instructions
- Vague router operations that may contain multiple internal process steps
- Possible equivalent operations across routers
- Product-specific differences that may affect the reference

## Blocking Open Questions

Blocking open questions are unresolved items that could make the final reference misleading for downstream manufacturing skills.

An unresolved item is blocking when it affects one or more of these:

1. Normal operation sequence
2. Operation meaning
3. Operation-to-machine or operation-to-equipment mapping
4. Work center ownership
5. Manual vs machine ownership
6. Inspection, test, review, or acceptance-point identity
7. Whether a step is standard flow vs optional/rework/MRB
8. Whether evidence, records, or logs are actually retained vs only possible
9. Conflicts between router data, machine-list data, operation instructions, and user notes

Blocking open questions include:

- Conflicting machine or equipment mappings
- Low-confidence operation-to-machine mappings that affect normal flow or evidence routing
- Ambiguous generic operations such as `Process`, `Inspect`, `Verify`, `Build`, `Run`, or `Check` when they represent meaningful production flow
- Unknown or blank work centers on meaningful production operations
- Active machines or equipment not mapped to any operation when they appear relevant to the uploaded flow
- Router operations with no likely machine, equipment, manual, inspection, test, review, or administrative owner
- Optional, rework, or MRB operations mixed into the normal operation flow
- Evidence, record, or log retention assumptions that would be stated as fact but are only possible or unconfirmed
- Conflicts between router data, machine-list data, operation instructions, and user notes

## Question Quality Rules

- Questions should be specific and targeted.
- Prefer yes/no or choose-between questions when possible.
- Tie each question to the exact operation, work center, or machine involved.
- Include the current proposed interpretation when helpful.
- Ask only about items that affect the usefulness or correctness of `shop-reference.md`.

## Good Question

"Does Op 050 Solder Reflow use the VAC 545 Vapor Phase machine, or is that operation handled by another reflow process?"

## Bad Question

"Explain your shop flow."

## Question Format

Use this structure when practical:

- Source item: operation, work center, machine, or product family
- Current interpretation
- Specific question
- Suggested answer options when possible

Example:

| Item | Current Interpretation | Question | Suggested Answers |
|---|---|---|---|
| Op 050 Solder Reflow | Possibly uses VAC 545 Vapor Phase | Does Op 050 use VAC 545, another reflow machine, or a manual soldering process? | VAC 545 / another reflow machine / manual process / unknown |

## Draft And Final Reference Rule

Open questions do not stop review-stage drafting, but blocking open questions do stop creation of any final reference file.

If blocking open questions remain, do not create, write, save, or present `reference.md` or `shop-reference.md`. Output `ShopContext Review - User Confirmation Needed` first and ask the blocking questions in the review response.

A user request to `generate reference.md`, `generate shop-reference.md`, `create the reference`, `write the reference`, or `save the reference` does not override the Blocking Review Gate.

Do not include unresolved blocking questions, blocking uncertainty, unresolved blocking mappings, or a questions section inside final `reference.md` or final `shop-reference.md`.

If the user explicitly asks to proceed without answering blocking questions, create or present only a clearly labeled draft-only reference, such as `shop-reference-draft.md`; do not create final `reference.md` or final `shop-reference.md`.

If only non-blocking questions remain and the user asks for a draft, include the best-supported draft content and clearly label uncertain, low-confidence, or unmapped items.

The draft should remain usable by AI, but users should be able to see which parts still need confirmation.

Do not remove an open question until the user or source documents resolve it.

Open questions belong in the ShopContext Review stage. Do not include a standalone open-questions section in the final `reference.md` or final `shop-reference.md`.

If non-blocking uncertainty remains after user review, mark it briefly inside the relevant final section using `Unknown`, `appears to`, or `likely`.

Low confidence does not stop drafting. Low confidence does stop finalization.

Do not create, write, save, or present final `reference.md` or final `shop-reference.md` while blocking open questions remain unanswered.

A final `reference.md` or final `shop-reference.md` is only allowed after blocking open questions are answered, or after ShopContext determines there are no blocking open questions.

If blocking open questions exist, output `ShopContext Review - User Confirmation Needed` instead of final `reference.md` or final `shop-reference.md`.

If the user does not answer clearly, output `ShopContext Review - Still Blocked`, list the remaining blocking questions, and do not create final `reference.md` or final `shop-reference.md`.

If the user explicitly asks to proceed without answering blocking questions, create or present only `shop-reference-draft.md`, or a clearly labeled draft-only reference. Do not create final `reference.md` or final `shop-reference.md`.

Do not silently present uncertain mappings as final.

## Question Prioritization For User Setup Mode

In User Setup Mode, do not list every possible open question.

Ask the minimum useful set of questions needed to resolve high-impact uncertainty.

Prioritize questions about:

1. Broad operation-to-machine mappings.
2. Vague operations with missing or ambiguous attached instructions.
3. Machines with multiple possible operations.
4. Operations with no mapped machine/equipment.
5. Work center meanings when the codes are not self-explanatory.
6. Quality gates, inspection points, and test points.
7. Manual vs machine-supported operations.
8. Confirmed records/logs only when a source hints at retention or the user needs the reference to preserve them.

Avoid low-value questions in the first pass.

Do not ask more than 10 questions unless the user requests a deeper review.

Optional enrichment questions, such as which records/logs are retained, should be clearly marked optional.
