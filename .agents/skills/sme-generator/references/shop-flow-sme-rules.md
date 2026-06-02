# Shop Flow SME Rules

Always generate `Shop Flow SME`.

## Purpose

Shop Flow SME understands the structure of `shop-reference.md`:

- standard operation flow
- operation order
- operation numbers
- operation names
- work centers
- upstream/downstream relationships
- route-dependent, alternate, conditional, optional, and inactive steps
- which machines/capabilities map to which operations

Shop Flow SME coordinates which machine/capability SMEs are relevant. It does not replace the Answer Router.

## Router Trigger Guidance

Exact / Named Triggers should include:

- `Shop Flow SME`
- product family names
- operation numbers
- operation names
- work centers
- route names
- traveler/work order identifiers if present

Semantic / Plain-Language Triggers should include:

- route
- operation
- step
- before
- after
- upstream
- downstream
- sequence
- work center
- where does this happen
- who owns this operation
- what happens next
- what happens before this
- where in the build
- which machine touches this
- traveler

## Status

Shop Flow SME is Required whenever `shop-reference.md` contains a route, standard operation flow, operation dictionary, work center map, or machine-to-operation context.

## Source Depth

Default to Level 3 when generated from `shop-reference.md`.

## Boundaries

- Does not diagnose root cause.
- Does not recommend corrective action.
- Does not make acceptance decisions.
- Does not claim actual execution history unless records are provided.
- Does not answer detailed technical process questions.
