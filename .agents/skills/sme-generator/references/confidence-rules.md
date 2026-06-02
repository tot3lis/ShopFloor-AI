# Confidence Rules

Assign confidence based on how clearly `shop-reference.md` supports the SME.

## High

Use High when:

- `Shop Flow SME` is generated from a structured route/operation reference.
- `Inspection SME` is generated from explicit inspection, quality gate, test, or acceptance sections.
- a named machine/capability is directly tied to a standard route operation.
- the source explicitly confirms the machine/capability relationship.

## Medium

Use Medium when:

- a named machine/capability is tied to alternate, route-dependent, conditional, special, or when-required use.
- the operation supports the machine/capability but the mapping is incomplete.
- inspection wording is generic but still supported by quality-gate context.

## Low

Use Low when:

- a named machine/capability is listed but not tied to a provided route.
- the item is backup-only, inactive, present in shop but not used, or weakly linked.
- the source suggests possible relevance but does not confirm use.

## Unknown

Use Unknown when:

- the source names an item but gives no clear capability, work center, operation, or status.

## Guardrails

- When in doubt, choose the lower confidence and add an open question.
- Do not raise confidence based on general industry knowledge.
- Do not use CCA/electronics assumptions to resolve non-CCA shops.
