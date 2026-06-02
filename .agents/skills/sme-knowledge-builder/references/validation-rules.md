# Validation Rules

Run this validation before finishing a knowledge-builder task or after editing the skill.

## Skill Structure

- `SKILL.md` has valid YAML front matter.
- Front matter contains only `name` and `description`.
- `name` is `sme-knowledge-builder`.
- `description` is concise, triggerable, and includes exclusions.
- Required reference files exist under `references/`.

## Output Completeness

- `knowledge-package-registry.md` is created or updated.
- `sme-knowledge-map.md` is created or updated.
- Each package has `knowledge-packages/<package-name>/knowledge-pack.md`.
- Each package has `knowledge-packages/<package-name>/source-map.md`.
- `sme-knowledge-map.md` maps every discovered SME, even if some have no package attachment.
- `knowledge-package-registry.md` uses `Input Mapping Confidence` and `Technical Source Confidence`, not only `Source Confidence`.
- `sme-knowledge-map.md` separates `Primary Packages` and `Context Packages`.

## Domain-Agnostic Behavior

- Package derivation is input-driven.
- No hardcoded domain package names appear as default outputs.
- No reflow, SMT, electronics, CCA, machining, molding, welding, heat treat, assembly, packaging, inspection, or other process appears unless input files justify it.
- Examples are clearly labeled as examples and are not used as default package targets.

## Source And Claim Quality

- Source tiering is generic manufacturing-wide.
- A targeted public-source search is attempted for sourceable process, equipment-family, material, inspection-method, and machine-model packages when network/search access is available.
- Source maps include research queries used when public search was performed.
- Source maps include title, type, tier, location, contribution, source confidence, limitations, and source basis.
- Source maps label generated SME shell, `sme-registry.md`, `shop-reference.md`, public source actually gathered, public-source placeholder, user-uploaded document, and actual record/log distinctly when present.
- Public-source placeholders are labeled clearly.
- Technical Source Confidence is not medium/high when sources are only placeholders.
- Placeholder confidence remains only when source gathering was blocked, intentionally not performed, or credible package-specific sources were unavailable.
- Public claims are not treated as shop-approved truth.
- Tier 6 sources are labeled anecdotal.
- Machine-specific claims are conservative and source-supported.
- Exact-machine claims, machine-family claims, process-family claims, and shop-specific facts are separated when their source support differs.
- Packages include meaningful technical depth: principles, variables, process-window concepts, failure modes, mechanisms, heuristics, and terminology appropriate to source support.
- Unsupported topics are listed as missing package opportunities or deferred registry entries.
- Context packages do not imply process ownership or expand SME authority.

## Architecture Boundaries

- SME Manager behavior is unchanged.
- Generated SME shells are not edited unless explicitly requested.
- The skill does not become an RCCA tool, evidence-request generator, troubleshooting checklist generator, corrective-action generator, or accept/reject decision tool.
- Layer 5 uploaded-document upgrades are documented as a future layer unless explicitly requested.
