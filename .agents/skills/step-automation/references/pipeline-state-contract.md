# Pipeline State Contract

## State File Path

`.shop-ai/state.md`

## Purpose

The state file gives the wrapper a deterministic, human-readable view of where the shop onboarding pipeline stands.

Use plain markdown. Keep the tracked fields exact and easy to edit.

## Required Fields

```markdown
# Shop AI State

- onboarding_status: needs_inputs | needs_shopcontext_answers | ready_for_generation | generating_smes | generating_knowledge | ready_for_questions
- shop_reference: missing | draft | finalized
- sme_generation: not_started | complete
- knowledge_builder: not_started | complete
- question_mode: disabled | enabled
- last_updated:
- notes:
```

## Field Meanings

`onboarding_status`

- `needs_inputs`: no usable messy shop inputs or `shop-reference.md` found.
- `needs_shopcontext_answers`: ShopContext has mandatory blocking questions and the pipeline must stop until the user answers.
- `ready_for_generation`: `shop-reference.md` is finalized and SME generation can run.
- `generating_smes`: SME Generator is currently being used or should be run next.
- `generating_knowledge`: SME Knowledge Builder is currently being used or should be run next.
- `ready_for_questions`: Layer 1-4 outputs exist and normal shop questions should use SME Manager behavior by default.

`shop_reference`

- `missing`: no `shop-reference.md`.
- `draft`: ShopContext draft exists or mandatory questions remain open.
- `finalized`: `shop-reference.md` exists and is ready for SME generation.

`sme_generation`

- `not_started`: `sme-registry.md` or `smes/*.md` is missing.
- `complete`: `sme-registry.md` and at least one SME shell under `smes/` exist.

`knowledge_builder`

- `not_started`: `knowledge-package-registry.md` or `sme-knowledge-map.md` is missing.
- `complete`: Layer 4 registry and map exist, with package folders where applicable.

`question_mode`

- `disabled`: normal shop questions should continue onboarding or ask for missing setup.
- `enabled`: normal manufacturing questions route to SME Manager behavior by default.

## State Update Rules

- Update state after each successful pipeline step.
- If a blocking question appears, set `onboarding_status: needs_shopcontext_answers` and `question_mode: disabled`.
- If all required outputs exist, set `onboarding_status: ready_for_questions` and `question_mode: enabled`.
- Do not mark `ready_for_questions` unless these exist:
  - `shop-reference.md`
  - `sme-registry.md`
  - `smes/*.md`
  - `sme-knowledge-map.md`
  - `knowledge-package-registry.md`

## Notes Field

Use short notes for:

- mandatory ShopContext questions asked
- missing inputs
- generation blockers
- manually supplied user answers
- validation status
- known limitations such as missing manuals, specs, procedures, or records
