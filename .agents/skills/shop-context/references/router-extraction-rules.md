# Router Extraction Rules

Use these rules when extracting manufacturing context from routers, work orders, travelers, operation lists, attached operation instructions, or similar process documents.

## Extracted Fields

Extract the following when present:

- Operation number
- Operation name
- Work center
- Sequence
- Product family hints
- Inspection or test points
- Manual or administrative steps
- Special notes
- Material, process, setup, or acceptance notes
- Attached operation instruction references
- Internal process steps found inside attached operation instructions
- Explicitly confirmed records, logs, forms, or result files

## Attached Operation Instructions

Treat attached operation instructions as major inputs. They may be PDFs, Word documents, markdown files, text files, copied document content, or instruction text embedded in a work order packet.

Operation instructions often contain the real process detail hidden behind vague router operation names. For example, a router operation named `Process Secondary Side` may contain internal steps such as solder paste application, pick-and-place, vapor phase reflow, wash, and bake.

When instructions are provided:

- Link each instruction to the exact operation number and operation name when possible.
- Preserve the router operation as the sequence container.
- Summarize the instruction into internal process steps for that operation.
- Preserve important source language such as machine names, asset IDs, fixture names, materials, programs, times, temperatures, acceptance criteria, and signoff language.
- Do not copy the full instruction into the reference.
- If a record, log, form, result file, or checklist is explicitly required or retained by the instruction, capture it as a confirmed record/log for the relevant operation.
- If the instruction cannot be confidently linked to an operation, flag it for user review.

## Atomicity Rule

Do not assume router operations are atomic.

The router or work order gives the operation label, operation number, sequence, and often the work center. Attached instructions may show that one router operation contains many internal process steps.

Keep both levels visible:

- Router operation: the named operation in the planned flow.
- Internal process steps: the summarized work inside that operation, usually from attached instructions or detailed notes.

## Operation Numbers

- Preserve operation numbers exactly as shown.
- Do not normalize leading zeroes away.
- Do not rewrite shop operation numbering conventions.
- If two routers use different numbers for similar work, keep both numbers and flag possible equivalence.

## Operation Names

- Preserve operation names exactly as shown.
- Add a plain-English meaning separately when supported.
- Do not assume two operations are the same just because names are similar.
- If operation names differ but appear to perform the same function, group them as possible equivalents and flag for review.

## Work Centers

- Extract work centers exactly as shown.
- Keep work center codes and descriptions if both are present.
- If a work center is missing, mark it unknown instead of deriving one without support.

## Sequence

- Determine operation sequence from operation number order, router line order, explicit predecessor/successor fields, or step sequence fields.
- If these conflict, preserve the conflict in notes and create an open question.
- Do not reorder operations solely to match a generic manufacturing flow.

## Product Family Hints

Product family hints may come from:

- Part numbers
- Assembly names
- Router names
- Work order descriptions
- Common prefixes or suffixes
- User notes

Label inferred product families as inferred unless explicitly named.

## Inspection And Test Points

Identify inspection or test points from terms such as:

- Inspection
- Final inspection
- In-process inspection
- Quality
- AOI
- X-ray
- Electrical test
- Functional test
- ATP
- ESS
- Burn-in
- Verification
- Acceptance

Do not treat every operation as an inspection point. Some operations may include checks without being formal quality gates.

## Manual Or Administrative Steps

Identify likely manual or administrative steps from terms such as:

- Kit
- Material issue
- Setup
- Hand solder
- Touch-up
- Rework
- Manual assembly
- Review
- Stamp
- Signoff
- Pack
- Ship
- Close work order

Flag manual status as uncertain when the source does not clearly say whether a machine is involved.

## Alternate, Optional, And Rework Operations

If the router includes alternate, optional, conditional, rework, repair, or disposition operations, preserve them separately from the standard operation flow.

Do not treat rework or optional operations as part of the normal route unless the source clearly says they are standard.

Label these operations as:

- Standard
- Alternate
- Optional
- Rework / repair
- Administrative / closeout
- Unknown route role

If the route role is unclear, preserve the operation and create an open question.

## Grouping Similar Operations Across Routers

When multiple routers are provided:

- Group operations only when operation number, name, work center, and process meaning support the grouping.
- Preserve product-specific differences.
- Keep alternate operation numbers visible.
- Use "possible equivalent" when the function appears similar but the source does not prove equivalence.
- Avoid flattening distinct product routes into one fake universal route.

## Confirmed Records / Logs

Do not create generic evidence-source lists from router or operation names.

Only capture records/logs/forms/results when the source explicitly says they are created, retained, attached, reviewed, signed, exported, or used.

Examples of confirmed records/logs may include a named traveler signoff, required checklist, test result file, AOI report, bake log, inspection form, or serialized data export, but only when source-supported.

Place confirmed records/logs in the relevant Operation Step Summary in the final reference.

## Source Limits

Treat routers as process skeletons, not complete evidence sources. Routers show intended flow and control points, but they do not prove what happened on a specific date or unit.

Routers describe the intended or planned manufacturing flow. They do not prove that a specific unit actually followed every listed operation, skipped an operation, or experienced a delay, rework loop, machine issue, or operator deviation.

If actual execution is needed, the user must provide actual execution records. ShopContext does not perform dynamic data integration or execution-history analysis.
