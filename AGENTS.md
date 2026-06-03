# ShopFloor AI Agent Instructions

This repo is an integrated manufacturing AI skill stack.

Use `$shopfloor-ai` as the front door for onboarding messy shop inputs and coordinating the Layer 1-4 pipeline.

Public MVP routing rule: `shopfloor-ai` is the top-level entrypoint. Explicit `run shopfloor-ai`, `$shopfloor-ai`, or `use shopfloor-ai` routes to `.agents/skills/shopfloor-ai/`. Explicit product command beats implicit file match, so router exports, machine lists, work orders, travelers, and operation files attached to that command remain inputs to ShopFloor AI. Lower-level skills are internal unless explicitly requested by the user or invoked by the orchestrator.

Primary MVP onboarding path: the user drops messy shop files directly into the Codex chat or pastes file contents into the prompt, then says `run shopfloor-ai`. Treat chat-attached and pasted files as valid primary onboarding inputs. An `inputs/` folder is optional, not required.

Repo-local skills:

- `.agents/skills/shop-context/`
- `.agents/skills/sme-generator/`
- `.agents/skills/sme-manager/`
- `.agents/skills/sme-knowledge-builder/`
- `.agents/skills/shopfloor-ai/`

When `.shop-ai/state.md` is in `ready_for_questions` state, normal manufacturing shop questions should be answered using SME Manager behavior by default, even if the user does not explicitly invoke `$sme-manager`.

The manager remains an orchestrator. It should select SMEs, check linked knowledge packages after SME selection, let SMEs use their shells and linked packages, then synthesize a concise user-facing answer.

Public/generic knowledge packages must not override shop-specific SME shell facts, user-uploaded documents, actual evidence, or controlling acceptance criteria.

Do not make SME Manager the technical brain directly. Knowledge packages attach to SMEs.

Do not turn Layer 4 into an evidence checklist system. Layer 4 is technical knowledge enrichment.

Do not make root cause claims, corrective action recommendations, production capacity estimates, or accept/reject decisions without controlling evidence, authority, and criteria.

For public package work, do not commit local generated shop outputs from the repo root. Keep generated examples under `examples/` and keep local runtime state out of Git.
