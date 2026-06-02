# SME Manager Source Priority Rules

## Priority Order

1. `sme-registry.md`: primary routing index and SME status/confidence.
2. `smes/*.md`: primary answer source for the selected process area.
3. `smes/shop-flow-sme.md`: primary interface for route flow, operation sequence, and shop-context knowledge.
4. `sme-knowledge-map.md`: supporting source for identifying Layer 4 packages linked to selected SMEs.
5. `knowledge-package-registry.md` and `knowledge-packages/*`: selected SME invocation context only, not manager-owned technical authority.
6. `sme-coverage.md`: supporting source for coverage, gaps, confidence, operation-to-SME mapping, machine-to-SME mapping, and level-up priorities.
7. `shop-reference.md` or shop-specific Layer 1 references: fallback/audit only.

## Normal Answering

Do not use Layer 1 shop-reference files as the normal source for answering. The SME Manager should not reconstruct, relearn, or remap the shop from the full Layer 1 reference when Layer 2 outputs are present. Do not use `shop-reference.md` to silently fill normal answers.

Do not use Layer 4 knowledge packages as the manager's own technical knowledge base. Knowledge packages upgrade individual SMEs. The manager may use `sme-knowledge-map.md` to attach packages to selected SMEs, then synthesize the contributions those SMEs produce.

## When To Use Layer 1

Use Layer 1 only when:

- The user asks to audit or compare Layer 1 and Layer 2.
- The Layer 2 files are missing or contradictory.
- The task is fixture validation.
- The user explicitly asks for the original shop reference.
- Debug/routing validation requires checking Layer 1 against Layer 2.

When Layer 1 is used, say why if it affects confidence.

If SME shells are thin, say what is missing and recommend what to upload rather than silently deriving a stronger answer from `shop-reference.md`.

## Layer 4 Package Use

When `sme-knowledge-map.md` exists:

1. Select SMEs from `sme-registry.md` and `smes/*.md` first.
2. Check `sme-knowledge-map.md` only for the selected SMEs.
3. Attach linked primary packages to each selected SME invocation context.
4. Attach only highly relevant context packages when they directly support the user's question.
5. Carry package Technical Source Confidence and limitations into the SME invocation context.

Shop-specific SME shell facts outrank package content. Public or generic package knowledge cannot override shop-specific SME facts. Placeholder, not gathered, low, or otherwise weak Technical Source Confidence can support only bounded general reasoning.

## Confidence

Respect status and confidence from the registry and coverage map:

- `Required` and high confidence can be stated more directly.
- `Needs review`, `Optional`, and medium/low confidence need qualifiers.
- Shell-only SMEs can identify context and records, but should not invent technical interpretation.
- Package-supported SME contributions may add bounded technical reasoning, but only to the level supported by package source confidence.
