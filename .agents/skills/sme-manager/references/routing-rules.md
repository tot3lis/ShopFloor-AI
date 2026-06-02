# SME Manager Routing Rules

## Routing Order

1. Read `sme-registry.md`.
2. Identify direct SME matches by operation, machine, process area, record type, or quality gate.
3. Read the smallest relevant set of `smes/*.md`.
4. Include `smes/shop-flow-sme.md` when the question involves operation sequence, before/after flow, route scope, standard versus conditional operations, or shop-context routing.
5. If `sme-knowledge-map.md` exists, check it only for the selected SMEs to identify linked primary packages and highly relevant context packages.
6. Build per-SME invocation contexts from the selected SME shell plus linked package context. The manager does not reason directly from package content as the manager.
7. Ask each selected SME to produce a contribution from its own context.
8. Synthesize selected SME contributions into the user-facing answer.
9. Read `sme-coverage.md` when the question asks about missing coverage, confidence, first SME to improve, taxonomy gaps, or validation.
10. Use Layer 1 shop-reference files only for explicit audit/source-trace requests, missing or contradictory Layer 2 files, or debug/routing validation.

## SME Invocation Context

For each selected SME, include:

- Selected SME shell.
- Linked primary knowledge packages from `sme-knowledge-map.md`.
- Only highly relevant context packages that directly support the user's question.
- Package source confidence and limitations when available.

Each SME contribution should include:

- Shop-specific view from its SME shell.
- Technical view from linked knowledge packages.
- What the SME can say.
- What the SME cannot conclude.
- Confidence/source-depth note.

Shop-specific SME shell facts outrank generic package knowledge. Public or generic packages cannot override shop facts. Placeholder or weak Technical Source Confidence should only support bounded general reasoning.

## Common Routing Patterns

- Operation number question: Shop Flow SME plus any SME mapped to that operation.
- Machine or equipment question: SME mapped to the machine, plus Shop Flow SME when route impact matters, plus package context attached to the selected SME when available.
- Inspection or acceptance question: Inspection SME plus named inspection equipment SME when relevant, plus Shop Flow SME when timing matters. Do not make accept/reject decisions without criteria and evidence.
- Material availability or out-time question: Kitting / Material Availability SME.
- Rework or repair question: Rework SME only when the route or user question indicates repair.
- Level-up priority question: `sme-coverage.md`, `sme-registry.md`, and the candidate SME shells.

## Routing Privacy

Do not expose the route unless useful to the user. Convert routing into a natural answer.

Good:

> In this shop, Op 040 means vacuum bagging for the composite panel route, including a leak check before cure.

Avoid:

> I routed this to Shop Flow SME and Vacuum Bagging SME.

## Mode-Specific Routing Disclosure

- Default mode: hide routing mechanics. Give the shop answer.
- Explain mode: briefly name the main SME categories, files, and package categories if the user asks what the answer was based on.
- Debug/routing mode: list candidate SMEs, selected SMEs, rejected SMEs, source files, linked packages, package source confidence, trigger matches, and routing confidence only when explicitly requested.
- RCCA/corrective-action mode: route to evidence and criteria needs first; do not turn routing confidence into root cause confidence.

## Ambiguity Handling

If the user's wording could map to multiple product families or operations, answer what is known and ask for the missing discriminator only when needed.

For ambiguous operation numbers in multi-route shops, do not force one meaning. Answer compactly with the known route-specific meanings, then ask for the product family/router if needed. Example: "Op 040 depends on the route. For COMPOSITE-PANEL it is Vacuum Bag; for BONDED-BRACKET it is Assemble Bond. Give me the product family/router before treating Op 040 as one fixed process."

Prefer:

- "If this is the composite panel route..."
- "For the bonded bracket route..."
- "I would ask which part family and operation this came from."

Do not pretend the route is known when the SME files separate multiple routes.
