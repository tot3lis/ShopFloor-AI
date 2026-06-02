# Onboarding Flow

## Purpose

Define the deterministic setup flow for a manufacturing shop AI project.

The wrapper coordinates existing skills. It does not rewrite their behavior.

## Step 1: Detect Current State

Inspect the project root for:

- `shop-reference.md`
- `sme-registry.md`
- `smes/*.md`
- `sme-knowledge-map.md`
- `knowledge-package-registry.md`
- `knowledge-packages/*`
- `.shop-ai/state.md`
- `.shop-ai/onboarding-log.md`

Then update `.shop-ai/state.md` according to `pipeline-state-contract.md`.

## Step 2: Missing Shop Reference

If `shop-reference.md` does not exist:

1. Look for messy shop inputs in `inputs/`.
2. Include user-provided uploaded or pasted files.
3. Use ShopContext behavior to create or review `shop-reference.md`.
4. If ShopContext identifies mandatory blocking questions, stop.
5. Ask only the mandatory questions.
6. Record the questions in `.shop-ai/onboarding-log.md`.
7. Set state:
   - `onboarding_status: needs_shopcontext_answers`
   - `shop_reference: draft`
   - `question_mode: disabled`

Do not show a long mapping draft unless ShopContext explicitly requires it.

## Step 3: Mandatory ShopContext Answers

When the user answers mandatory ShopContext questions:

1. Use ShopContext behavior to apply the answers.
2. Finalize `shop-reference.md`.
3. Record the answers in `.shop-ai/onboarding-log.md`.
4. Set state:
   - `onboarding_status: ready_for_generation`
   - `shop_reference: finalized`

## Step 4: Generate SMEs

If `shop-reference.md` exists but `sme-registry.md` or `smes/*.md` is missing:

1. Use SME Generator behavior.
2. Generate:
   - `sme-coverage.md`
   - `sme-registry.md`
   - `smes/*.md`
3. Set state while running:
   - `onboarding_status: generating_smes`
4. Set state when complete:
   - `sme_generation: complete`

## Step 5: Generate Knowledge Packages

If SME outputs exist but `sme-knowledge-map.md` or `knowledge-package-registry.md` is missing:

1. Use SME Knowledge Builder behavior.
2. Generate:
   - `knowledge-package-registry.md`
   - `sme-knowledge-map.md`
   - `knowledge-packages/*/knowledge-pack.md`
   - `knowledge-packages/*/source-map.md`
3. Set state while running:
   - `onboarding_status: generating_knowledge`
4. Set state when complete:
   - `knowledge_builder: complete`

## Step 6: Ready For Questions

When these exist:

- `shop-reference.md`
- `sme-registry.md`
- `smes/*.md`
- `sme-knowledge-map.md`
- `knowledge-package-registry.md`

Set state:

- `onboarding_status: ready_for_questions`
- `shop_reference: finalized`
- `sme_generation: complete`
- `knowledge_builder: complete`
- `question_mode: enabled`

Tell the user:

> The shop AI stack is ready. You can now ask normal shop questions in plain English.

## Blocking Rules

Stop and ask the user when:

- ShopContext has mandatory blocking questions.
- No messy input files or pasted inputs are available.
- Existing outputs contradict each other and the wrapper cannot safely continue.
- Required generated files are missing and the relevant underlying skill cannot be used.

Ask the smallest useful question set. Do not ask broad setup questions when the underlying skill only needs specific blocking answers.
