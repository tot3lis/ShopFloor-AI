# Pipeline State Contract

## State File Path

`.shop-ai/state.md`

Do not rename `.shop-ai/`; it remains the state folder for ShopFloor AI.

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
- `ready_for_questions`: Layer 1-4 outputs exist and normal shop questions should use SME Manager behavior by default. This state must not be written until all ready-state artifact checks pass.

`shop_reference`

- `missing`: no `shop-reference.md`.
- `draft`: ShopContext draft exists or mandatory questions remain open.
- `finalized`: `shop-reference.md` exists and is ready for SME generation.

`sme_generation`

- `not_started`: `sme-registry.md`, `sme-coverage.md`, or `smes/*.md` is missing.
- `complete`: `sme-registry.md`, `sme-coverage.md`, and at least one SME shell under `smes/` exist.

`knowledge_builder`

- `not_started`: `knowledge-package-registry.md`, `sme-knowledge-map.md`, or `knowledge-packages/*/knowledge-pack.md` is missing.
- `complete`: Layer 4 registry and map exist, with at least one `knowledge-packages/*/knowledge-pack.md` file where package generation is applicable.

`question_mode`

- `disabled`: normal shop questions should continue onboarding or ask for missing setup.
- `enabled`: normal manufacturing questions route to SME Manager behavior by default.

## State Update Rules

- Update state after each successful pipeline step.
- State updates must be incremental. Do not pre-write future completion states before the corresponding artifacts exist.
- If a blocking question appears, set `onboarding_status: needs_shopcontext_answers` and `question_mode: disabled`.
- After ShopContext completes without blockers, state may say `onboarding_status: ready_for_generation` and `shop_reference: finalized`, but it must keep `question_mode: disabled`.
- After SME Generator completes, state may say `sme_generation: complete`, but it must keep `question_mode: disabled`.
- After SME Knowledge Builder completes and ready-state artifact checks pass, and only then, set `onboarding_status: ready_for_questions` and `question_mode: enabled`.
- If all required outputs exist, set `onboarding_status: ready_for_questions` and `question_mode: enabled`.
- Do not mark `ready_for_questions` unless these exist:
  - `shop-reference.md`
  - `sme-registry.md`
  - `sme-coverage.md`
  - `smes/*.md`
  - `sme-knowledge-map.md`
  - `knowledge-package-registry.md`
  - `knowledge-packages/*/knowledge-pack.md`

## Execution Gates

Reading later-layer skill instructions or reference files is allowed during planning, contract review, or validation. Reading instructions is not execution.

Execution gates are hard:

- ShopContext must run first during onboarding.
- SME Generator must not run until finalized `shop-reference.md` exists and mandatory ShopContext questions are resolved.
- SME Knowledge Builder must not run until `sme-registry.md`, `sme-coverage.md`, and at least one `smes/*.md` file exist.
- Public-source Layer 4 research, source gathering, package derivation, package writing, source-map writing, and package-to-SME mapping all count as SME Knowledge Builder execution.
- SME Manager question mode must not answer normal shop questions until `onboarding_status: ready_for_questions` and `question_mode: enabled` are valid.

## Onboarding Log Rules

Update `.shop-ai/onboarding-log.md` incrementally after each completed stage, or write the final log only at the actual end of Layer 4.

The log must not claim future stages are complete before their output artifacts exist. If timestamps are recorded, the final ready entry must correspond to the end of SME Knowledge Builder output creation, not the end of ShopContext.

## Notes Field

Use short notes for:

- mandatory ShopContext questions asked
- missing chat attachments, pasted inputs, or optional `inputs/` files
- generation blockers
- manually supplied user answers
- validation status
- known limitations such as missing manuals, specs, procedures, or records
