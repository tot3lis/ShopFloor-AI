# Operation-Machine Mapping Rules

Use these rules to propose operation-to-machine and operation-to-equipment mappings from routers, work centers, machine lists, attached operation instructions, and user notes.

The skill must never treat a weak mapping as fact.

## Mapping Types

## Direct Name Match

Use when operation name and machine name or type directly match. Example: Operation `AOI` and machine `Koh Young AOI`.

## Work Center Match

Use when the operation and machine share the same work center, and the machine capability is consistent with the operation.

## Instruction Step Match

Use when an attached operation instruction names a machine, equipment item, fixture, station, program, tool, or process step inside a router operation.

This can be High confidence when the instruction is clearly linked to the operation and explicitly names the equipment or process.

## Process Type Match

Use when the operation name and machine capability align even if work center is missing or different. Example: `Solder Reflow` and `VAC 545 Vapor Phase`.

## User-Provided Mapping

Use when the user explicitly states that a machine supports an operation. This can be High confidence unless the user note conflicts with a source document.

## Ambiguous Mapping

Use when more than one machine could support the operation, or when the source supports only a weak relationship.

## No Mapping Found

Use when no machine can be responsibly linked to the operation. Keep the operation visible and create an open question when the mapping matters.

## Manual Operation Rule

Some operations may not have a dedicated machine.

If an operation is manual, human-judgment-based, administrative, inspection-only, documentation-based, or handling-based, do not force a machine mapping.

Use `No dedicated machine identified` when appropriate.

Only suggest a manual bench, station, or tool if the source documents or user notes support it. Otherwise, flag the operation for review.

## Non-Atomic Operation Rule

Do not assume one router operation maps to one machine.

One router operation may contain multiple internal process steps and multiple machines or equipment items. For example, a vague operation such as `Process Secondary Side` may include print, pick-and-place, vapor phase, wash, and bake steps.

In review output, map equipment to the router operation and, when supported, to the internal process step.

In final `shop-reference.md`, fold these mappings into `## 4. Operation Step Summaries` and keep the Machine / Equipment Dictionary concise.

## Source / Product Context For Ambiguous Mappings

When multiple routers or products reuse the same operation number for different meanings, include a `Source`, `Product`, or `Route` column in mapping tables.

Use this only when it reduces ambiguity.

Do not merge operations across products unless the source documents or user confirms they are equivalent.

## Review Mapping Table Format

Use this table when presenting proposed mappings during review:

| Operation # | Operation Name | Internal Step | Work Center | Suggested Machine / Equipment | Mapping Basis | Confidence | Needs User Review? |
|---|---|---|---|---|---|---|---|
| 020 | SMT Print | Solder paste print | SMT | DEK Horizon | Instruction step + work center match | High | No |
| 030 | Pick and Place | Component placement | SMT | MY200 | Process type + machine name match | High | No |
| 040 | AOI | Inspection review | Inspection | Koh Young AOI | Direct name match | High | No |
| 050 | Solder Reflow | Vapor phase reflow | Solder | VAC 545 Vapor Phase | Process type match | Medium | Yes |
| 060 | Final Inspection | Manual visual inspection | Quality | Manual inspection bench | Manual operation support | Low | Yes |

## Mapping Rules

- Assign confidence per mapping.
- Separate operation extraction confidence from machine mapping confidence.
- Do not upgrade confidence because a mapping seems convenient.
- If the operation has multiple possible machines, list all candidates.
- If the machine has no clear operation, keep it in the machine dictionary and flag it as unmapped.
- If the router and machine list conflict, preserve the conflict and ask a targeted question.
- Low or unknown confidence must create an open question.
- Do not include a standalone machine-to-operation map in the final reference.
- Fold final mappings into Operation Step Summaries and the Machine / Equipment Dictionary.
