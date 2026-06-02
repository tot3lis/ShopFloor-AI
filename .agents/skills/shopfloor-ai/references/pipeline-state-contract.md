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

- onboarding_status: no_shop_inputs | awaiting_shopcontext_confirmations | shop_reference_finalized | sme_generation_complete | knowledge_builder_complete | ready_for_questions
- shop_reference: missing | draft | finalized
- shop_reference_status: missing | draft | review_needed | finalized
- sme_generation: not_started | complete
- knowledge_builder: not_started | complete
- question_mode: disabled | enabled
- last_updated:
- notes:
```

## Field Meanings

`onboarding_status`

- `no_shop_inputs`: no usable messy shop inputs or finalized `shop-reference.md` found.
- `awaiting_shopcontext_confirmations`: ShopContext has mandatory blocking questions and the pipeline must stop until the user answers.
- `shop_reference_finalized`: `shop-reference.md` exists, ShopContext blocking questions are resolved, and SME generation can run.
- `sme_generation_complete`: `sme-registry.md`, `sme-coverage.md`, and at least one SME shell exist.
- `knowledge_builder_complete`: Layer 4 registry/map/package artifacts exist, but final ready-state validation has not yet been written.
- `ready_for_questions`: Layer 1-4 outputs exist and normal shop questions should use SME Manager behavior by default. This state must not be written until all ready-state artifact checks pass.

Older local state files may use these legacy aliases: `needs_inputs`, `needs_shopcontext_answers`, `ready_for_generation`, `generating_smes`, and `generating_knowledge`. When updating state, rewrite them to the current values above.

`shop_reference`

- `missing`: no `shop-reference.md`.
- `draft`: ShopContext draft exists or mandatory questions remain open.
- `finalized`: `shop-reference.md` exists and is ready for SME generation.

`shop_reference_status`

- `missing`: no ShopContext output has been created.
- `draft`: ShopContext draft-only output exists, or a draft reference exists without finalization evidence.
- `review_needed`: ShopContext produced `ShopContext Review - User Confirmation Needed`, `ShopContext Review - Still Blocked`, a `Blocking Open Questions` section, or equivalent mandatory blocking questions.
- `finalized`: final `shop-reference.md` exists and ShopContext has resolved or found no blocking questions.

`shop_reference_status` is the downstream gate. `shop-reference.md` file existence does not equal finalization.

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
- If a blocking question appears, set `onboarding_status: awaiting_shopcontext_confirmations`, `shop_reference: draft`, `shop_reference_status: review_needed`, and `question_mode: disabled`.
- After ShopContext completes without blockers, state may say `onboarding_status: shop_reference_finalized`, `shop_reference: finalized`, and `shop_reference_status: finalized`, but it must keep `question_mode: disabled`.
- After SME Generator completes, state may say `onboarding_status: sme_generation_complete` and `sme_generation: complete`, but it must keep `question_mode: disabled`.
- After SME Knowledge Builder completes and ready-state artifact checks pass, and only then, set `onboarding_status: ready_for_questions` and `question_mode: enabled`.
- If all required outputs exist, set `onboarding_status: ready_for_questions` and `question_mode: enabled` only if `shop_reference_status: finalized`.
- Do not mark `ready_for_questions` unless these exist:
  - `shop-reference.md`
  - `sme-registry.md`
  - `sme-coverage.md`
  - `smes/*.md`
  - `sme-knowledge-map.md`
  - `knowledge-package-registry.md`
  - `knowledge-packages/*/knowledge-pack.md`
- Do not mark `ready_for_questions` if `.shop-ai/onboarding-log.md` records unresolved ShopContext blocking questions.
- `question_mode` must be `disabled` for every state except `ready_for_questions`.

## ShopContext Review-Gate Signals

The orchestrator must treat any of these ShopContext outputs as blocking:

- `ShopContext Review - User Confirmation Needed`
- `ShopContext Review - Still Blocked`
- `Blocking Open Questions`
- mandatory blocking questions
- unresolved confirmations
- low-confidence mappings that ShopContext labels as blocking or requiring user review
- draft-only references such as `shop-reference-draft.md`

When any of these signals appear, write `shop_reference_status: review_needed`, record the blocking questions in `.shop-ai/onboarding-log.md`, show only the blocking questions by default, and stop before SME Generator.

## Execution Gates

Reading later-layer skill instructions or reference files is allowed during planning, contract review, or validation. Reading instructions is not execution.

Execution gates are hard:

- ShopContext must run first during onboarding.
- SME Generator must not run until final `shop-reference.md` exists, `shop_reference_status: finalized` is recorded, and mandatory ShopContext questions are resolved.
- SME Knowledge Builder must not run until `sme-registry.md`, `sme-coverage.md`, and at least one `smes/*.md` file exist.
- Public-source Layer 4 research, source gathering, package derivation, package writing, source-map writing, and package-to-SME mapping all count as SME Knowledge Builder execution.
- SME Manager question mode must not answer normal shop questions until `onboarding_status: ready_for_questions` and `question_mode: enabled` are valid.

## Resume Rules

When `onboarding_status: awaiting_shopcontext_confirmations` or `shop_reference_status: review_needed`:

1. Read the stored blocking questions from `.shop-ai/onboarding-log.md` or `.shop-ai/state.md`.
2. Treat the user's next answers as ShopContext confirmation input.
3. Use ShopContext behavior to apply the answers and finalize `shop-reference.md`.
4. Set `shop_reference_status: finalized` only after ShopContext no longer has blocking questions.
5. Continue to SME Generator only after that finalized marker is written.

## Onboarding Log Rules

Update `.shop-ai/onboarding-log.md` incrementally after each completed stage, or write the final log only at the actual end of Layer 4.

The log must not claim future stages are complete before their output artifacts exist. If timestamps are recorded, the final ready entry must correspond to the end of SME Knowledge Builder output creation, not the end of ShopContext.

## Notes Field

Use short notes for:

- mandatory ShopContext questions asked
- unresolved ShopContext review-gate signals
- missing chat attachments, pasted inputs, or optional `inputs/` files
- generation blockers
- manually supplied user answers
- validation status
- known limitations such as missing manuals, specs, procedures, or records
