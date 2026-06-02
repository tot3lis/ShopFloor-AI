# Onboarding Flow

## Purpose

Define the deterministic setup flow for a manufacturing shop AI project.

The wrapper coordinates existing skills. It does not rewrite their behavior.

## Planning Vs Execution Boundary

The wrapper may read later-layer skill files and reference files during planning, validation, or contract inspection. Reading instructions is allowed before the matching layer runs.

Execution is different from planning. Do not execute a layer until its required upstream artifacts exist.

Public-source Layer 4 research, source gathering, package derivation, package writing, source-map writing, and package-to-SME mapping all count as SME Knowledge Builder execution. They must not begin until SME Generator outputs exist.

## Step 1: Detect Current State

Inspect the project root for:

- files attached in the current Codex/chat session
- files pasted into the current prompt
- optional files under `inputs/`
- `shop-reference.md`
- `sme-registry.md`
- `sme-coverage.md`
- `smes/*.md`
- `sme-knowledge-map.md`
- `knowledge-package-registry.md`
- `knowledge-packages/*`
- `.shop-ai/state.md`
- `.shop-ai/onboarding-log.md`

Then update `.shop-ai/state.md` according to `pipeline-state-contract.md`.

During state detection, do not infer completion from intent. Only mark a stage complete when the required output artifacts already exist.

During state detection, do not infer ShopContext completion from `shop-reference.md` alone. Downstream layers require:

- final `shop-reference.md` exists
- `.shop-ai/state.md` records `shop_reference_status: finalized`
- `.shop-ai/onboarding-log.md` has no unresolved ShopContext blocking questions
- the latest ShopContext result did not contain `ShopContext Review - User Confirmation Needed`, `ShopContext Review - Still Blocked`, or `Blocking Open Questions`

## Step 2: Missing Shop Reference

If `shop-reference.md` does not exist:

1. Say: "Using ShopContext to generate the shop reference file."
2. Look first for files attached in the current Codex/chat session.
3. Include files or data pasted into the current prompt.
4. Look for messy shop inputs in `inputs/` if the folder exists.
5. Treat `inputs/` as optional; do not require users to pre-organize files there.
6. If no attached files, pasted data, `inputs/` files, or existing `shop-reference.md` are available, ask the user to drop in routers, work orders, machine lists, operation exports, or shop notes. Do not proceed to SME Generator.
7. Use ShopContext behavior to create or review `shop-reference.md`.
8. If ShopContext outputs `ShopContext Review - User Confirmation Needed`, `ShopContext Review - Still Blocked`, `Blocking Open Questions`, or mandatory blocking questions, say: "ShopContext needs a few confirmations before setup can continue."
9. Stop and ask only the mandatory questions.
10. Record the questions in `.shop-ai/onboarding-log.md`.
11. Set state:
   - `onboarding_status: awaiting_shopcontext_confirmations`
   - `shop_reference: draft`
   - `shop_reference_status: review_needed`
   - `question_mode: disabled`
12. Do not run SME Generator, SME Knowledge Builder, public-source gathering, or question mode.

Do not show a long mapping draft unless ShopContext explicitly requires it.

If ShopContext creates or presents a draft-only reference such as `shop-reference-draft.md`, treat it as `shop_reference_status: draft`, not finalized.

If `shop-reference.md` is created without blockers, say: "Shop reference file created."

Then set state no further than:

- `shop_reference: finalized`
- `shop_reference_status: finalized`
- `onboarding_status: shop_reference_finalized`
- `sme_generation: not_started`
- `knowledge_builder: not_started`
- `question_mode: disabled`

Do not set `ready_for_questions` after ShopContext alone.

## Step 3: Mandatory ShopContext Answers

When the user answers mandatory ShopContext questions:

1. Use ShopContext behavior to apply the answers.
2. Finalize `shop-reference.md`.
3. Record the answers in `.shop-ai/onboarding-log.md`.
4. Say: "Shop reference file created."
5. Set state:
   - `onboarding_status: shop_reference_finalized`
   - `shop_reference: finalized`
   - `shop_reference_status: finalized`
   - `sme_generation: not_started`
   - `knowledge_builder: not_started`
   - `question_mode: disabled`

Do not proceed to SME Generator until the finalized `shop-reference.md` exists on disk, `shop_reference_status: finalized` is recorded, and blocking ShopContext questions are resolved.

## Step 4: Generate SMEs

If finalized `shop-reference.md` exists, `shop_reference_status: finalized` is recorded, no unresolved ShopContext blocking questions remain, and `sme-registry.md`, `sme-coverage.md`, or `smes/*.md` is missing:

1. Say: "Using SME Generator to generate shop SMEs."
2. Use SME Generator behavior.
3. Generate:
   - `sme-coverage.md`
   - `sme-registry.md`
   - `smes/*.md`
4. Set state while running:
   - keep `onboarding_status: shop_reference_finalized`
5. Set state when complete:
   - `onboarding_status: sme_generation_complete`
   - `sme_generation: complete`
   - `knowledge_builder: not_started`
   - `question_mode: disabled`
6. Say: "Shop SMEs generated."

SME Generator is complete only when all of these exist:

- `sme-registry.md`
- `sme-coverage.md`
- at least one `smes/*.md` file

Do not set `ready_for_questions` after SME Generator alone.

If `shop_reference_status` is `missing`, `draft`, or `review_needed`, Step 4 is forbidden even when `shop-reference.md` exists.

## Step 5: Generate Knowledge Packages

If SME outputs exist but `sme-knowledge-map.md`, `knowledge-package-registry.md`, or `knowledge-packages/*/knowledge-pack.md` is missing:

1. Say: "Using SME Knowledge Builder to generate knowledge packages."
2. Use SME Knowledge Builder behavior.
3. Generate:
   - `knowledge-package-registry.md`
   - `sme-knowledge-map.md`
   - `knowledge-packages/*/knowledge-pack.md`
   - `knowledge-packages/*/source-map.md`
4. Set state while running:
   - keep `onboarding_status: sme_generation_complete`
5. Set state when complete:
   - `onboarding_status: knowledge_builder_complete`
   - `knowledge_builder: complete`
6. Say: "Knowledge packages generated."

SME Knowledge Builder may run only after all of these exist:

- `sme-registry.md`
- `sme-coverage.md`
- at least one `smes/*.md` file

SME Knowledge Builder is complete only when all of these exist:

- `knowledge-package-registry.md`
- `sme-knowledge-map.md`
- at least one `knowledge-packages/*/knowledge-pack.md` file

## Step 6: Ready For Questions

When these exist:

- `shop-reference.md`
- `.shop-ai/state.md` with `shop_reference_status: finalized`
- `sme-registry.md`
- `sme-coverage.md`
- `smes/*.md`
- `sme-knowledge-map.md`
- `knowledge-package-registry.md`
- `knowledge-packages/*/knowledge-pack.md`

Set state:

- `onboarding_status: ready_for_questions`
- `shop_reference: finalized`
- `sme_generation: complete`
- `knowledge_builder: complete`
- `question_mode: enabled`

Tell the user:

> ShopFloor AI is ready. You can now ask shop questions in plain English.

Do not pre-write this final state before the Layer 4 artifact checks pass.

Do not enter ready state when `.shop-ai/onboarding-log.md` records unresolved ShopContext blocking questions.

## Resume From ShopContext Review Gate

If state says `onboarding_status: awaiting_shopcontext_confirmations` or `shop_reference_status: review_needed`:

1. Read the blocking questions from `.shop-ai/onboarding-log.md` or `.shop-ai/state.md`.
2. Treat the user's answers as ShopContext confirmation input.
3. Use ShopContext behavior to update or create final `shop-reference.md`.
4. If any blocking questions remain, keep `shop_reference_status: review_needed`, keep `question_mode: disabled`, ask only the remaining blocking questions, and stop.
5. If blocking questions are resolved, set `shop_reference_status: finalized`, set `onboarding_status: shop_reference_finalized`, keep `question_mode: disabled`, then continue to SME Generator.

## Onboarding Log Rules

Update `.shop-ai/onboarding-log.md` after each completed stage, or write a final log only after Step 6 artifact checks pass.

The log must not claim that SME generation, SME Knowledge Builder, knowledge packages, or ready state are complete before their output artifacts exist. If timestamps are included, the final ready entry must correspond to the end of Layer 4, not the end of ShopContext.

## Blocking Rules

Stop and ask the user when:

- ShopContext has mandatory blocking questions.
- ShopContext outputs `ShopContext Review - User Confirmation Needed`, `ShopContext Review - Still Blocked`, or `Blocking Open Questions`.
- No chat-attached files, pasted inputs, `inputs/` files, or existing `shop-reference.md` are available.
- Existing outputs contradict each other and the wrapper cannot safely continue.
- Required generated files are missing and the relevant underlying skill cannot be used.

Ask the smallest useful question set. Do not ask broad setup questions when the underlying skill only needs specific blocking answers.
