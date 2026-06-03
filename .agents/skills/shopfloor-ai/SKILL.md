---
name: shopfloor-ai
description: Public/user-facing ShopFloor AI orchestrator and top-level entrypoint for the manufacturing Layer 1-4 workflow. Must trigger when the user says `run shopfloor-ai`, `$shopfloor-ai`, `use shopfloor-ai`, or asks to onboard or run ShopFloor AI. Use attached router exports, machine lists, work orders, travelers, operation files, pasted shop data, or `inputs/` files as inputs to this orchestrator, not as a reason to bypass it. Owns the full onboarding flow from `shop-reference.md` to SME shells to SME knowledge packs to SME Manager question mode. During onboarding, runs ShopContext as the first internal step, then SME Generator and SME Knowledge Builder, and routes ready-state shop questions to SME Manager behavior by default.
---

# ShopFloor AI

## Purpose

Act as the public/user-facing top-level orchestrator for the integrated manufacturing shop AI workflow.

This is the front door for the public MVP. It must be selected when the user explicitly says `run shopfloor-ai`, `$shopfloor-ai`, `use shopfloor-ai`, or asks to onboard or run ShopFloor AI.

Explicit product command beats implicit file match. Attached router exports, machine lists, work orders, travelers, operation files, and similar ShopContext-looking inputs are inputs to the ShopFloor AI orchestrator, not a reason to bypass it.

This skill does not replace, merge, or rewrite the Layer 1-4 skills. It coordinates them in order:

1. ShopContext creates or finalizes `shop-reference.md` from messy shop inputs.
2. SME Generator creates `sme-coverage.md`, `sme-registry.md`, and `smes/*.md`.
3. SME Knowledge Builder creates `knowledge-package-registry.md`, `sme-knowledge-map.md`, and `knowledge-packages/*`.
4. SME Manager answers normal shop questions after the project is ready.

During ShopFloor AI onboarding, call ShopContext as the first internal step.

## Anti-Bypass Rule

When the user explicitly invokes ShopFloor AI with `run shopfloor-ai`, `$shopfloor-ai`, `use shopfloor-ai`, or equivalent onboarding/run language, do not directly switch to ShopContext just because the input files look like ShopContext inputs. Use ShopFloor AI first, then let this orchestrator run ShopContext internally.

## Required State File

Use deterministic state from:

- `.shop-ai/state.md`

Read `references/pipeline-state-contract.md` before creating or updating the state file.

## Inputs

Possible user inputs:

- files attached in the current Codex/chat session
- files pasted into the prompt
- messy files in `inputs/`, if present
- pasted router data, machine lists, operation notes, user corrections, work center exports, asset lists, or inspection notes
- existing generated outputs in the project root

Public package documentation and examples are not shop inputs unless the user explicitly supplies them as shop evidence. Do not use `README.md`, `AGENTS.md`, `validation/`, `.agents/skills/`, `examples/`, or example generated outputs to resolve ambiguity in the user's attached, pasted, or `inputs/` shop files.

## Outputs

The wrapper may create or update:

- `.shop-ai/state.md`
- `.shop-ai/onboarding-log.md`
- `shop-reference.md` only through ShopContext behavior
- `sme-coverage.md`, `sme-registry.md`, and `smes/*.md` only through SME Generator behavior
- `knowledge-package-registry.md`, `sme-knowledge-map.md`, and `knowledge-packages/*` only through SME Knowledge Builder behavior

Do not directly rewrite Layer 1-4 behavior from this wrapper.

## Workflow

1. Read `references/pipeline-state-contract.md`.
2. Read `references/status-messages.md`.
3. Read or create `.shop-ai/state.md`.
4. Read `references/onboarding-flow.md`.
5. Inspect the project for generated outputs:
   - `shop-reference.md`
   - `sme-registry.md`
   - `sme-coverage.md`
   - `smes/*.md`
   - `sme-knowledge-map.md`
   - `knowledge-package-registry.md`
   - `knowledge-packages/*/knowledge-pack.md`
6. Inspect ShopContext finalization state before treating `shop-reference.md` as usable by downstream layers:
   - `.shop-ai/state.md` must record `shop_reference_status: finalized`.
   - `.shop-ai/onboarding-log.md` must not record unresolved ShopContext blocking questions.
   - The latest ShopContext result must not be `ShopContext Review - User Confirmation Needed` or `ShopContext Review - Still Blocked`.
   - Run the finalization audit in `references/onboarding-flow.md` against the latest ShopContext output and `shop-reference.md`.
   - `shop-reference.md` existence by itself never proves finalization.
7. If onboarding is incomplete, continue the pipeline in order and show short setup status messages from `references/status-messages.md`.
8. If all required outputs exist and `shop_reference_status: finalized`, set:
   - `onboarding_status: ready_for_questions`
   - `question_mode: enabled`
   only after the finalization audit passes.
9. For normal manufacturing shop questions while ready, follow `references/question-mode-routing.md` and answer using SME Manager behavior by default. Do not show pipeline setup status messages for normal questions.

## Planning Vs Execution Boundary

The wrapper may read later-layer skill files and reference files while planning the workflow, checking contracts, or understanding the required sequence.

Reading instructions is not execution.

Do not execute a layer until its required input artifacts and state gates exist:

- Do not run SME Generator until `shop-reference.md` exists, `.shop-ai/state.md` says `shop_reference_status: finalized`, mandatory ShopContext questions are resolved, and the finalization audit finds no unresolved blocking uncertainty.
- Do not treat `shop-reference.md` existence as finalization. Draft-only references, partial references, review outputs, or any ShopContext result with blocking questions are not valid Layer 2 inputs.
- Do not run SME Knowledge Builder until `sme-registry.md`, `sme-coverage.md`, and at least one `smes/*.md` shell exist.
- Public-source Layer 4 research, source gathering, package derivation, package writing, and knowledge-package mapping all count as SME Knowledge Builder execution.
- Do not use SME Manager question mode until `ready_for_questions` is valid according to `references/pipeline-state-contract.md`.

## Onboarding Behavior

If `shop-reference.md` does not exist:

- Say: "Using ShopContext to generate the shop reference file."
- Use ShopContext behavior.
- Collect messy inputs from current chat attachments, pasted prompt content, and/or `inputs/` if present.
- Treat user-provided chat attachments as the primary onboarding path.
- If no attached/pasted files, no files in `inputs/`, and no existing `shop-reference.md` exist, ask the user to drop in routers, work orders, machine lists, operation exports, or shop notes. Do not proceed to SME Generator.
- If ShopContext outputs `ShopContext Review - User Confirmation Needed`, `ShopContext Review - Still Blocked`, a `Blocking Open Questions` section, or any mandatory blocking questions, say: "ShopContext needs a few confirmations before setup can continue."
- Set `onboarding_status: awaiting_shopcontext_confirmations`, `shop_reference_status: review_needed`, and `question_mode: disabled`; record the exact blocking questions in `.shop-ai/onboarding-log.md`, ask only those mandatory questions, and stop.
- After ShopContext creates or updates `shop-reference.md`, run the finalization audit before recording `shop_reference_status: finalized` or starting SME Generator.
- If the audit finds unresolved blocking uncertainty in normal operation flow, operation-to-machine/equipment mapping, work center ownership, inspection/test mapping, or confirmed record/log claims, say: "ShopContext needs a few confirmations before setup can continue."; set `onboarding_status: awaiting_shopcontext_confirmations`, `shop_reference_status: review_needed`, and `question_mode: disabled`; record the audit questions in `.shop-ai/onboarding-log.md`; ask only those questions; and stop.
- Do not run SME Generator, SME Knowledge Builder, public-source gathering, or question mode while `shop_reference_status` is `missing`, `draft`, or `review_needed`.
- When the file is created/finalized, say: "Shop reference file created."

If ShopContext mandatory questions have been answered:

- Use ShopContext behavior to apply the answers.
- Finalize `shop-reference.md`.
- Record the answers in `.shop-ai/onboarding-log.md`.
- Record `shop_reference_status: finalized` in `.shop-ai/state.md` only after ShopContext has resolved the blocking questions and is allowed to produce final `shop-reference.md`.
- Set `shop_reference: finalized`.
- Set `onboarding_status: shop_reference_finalized`.
- Do not set `onboarding_status: ready_for_questions`.
- Do not set `question_mode: enabled`.

If `shop-reference.md` exists, `.shop-ai/state.md` records `shop_reference_status: finalized`, no ShopContext blocking questions remain, the finalization audit passes, and `sme-registry.md`, `sme-coverage.md`, or `smes/*.md` is missing:

- Say: "Using SME Generator to generate shop SMEs."
- Use SME Generator behavior automatically.
- Do not mark SME generation complete while running.
- Set `sme_generation: complete` only after `sme-registry.md`, `sme-coverage.md`, and at least one `smes/*.md` shell exist.
- Set `onboarding_status: sme_generation_complete` only after those SME artifacts exist.
- Say: "Shop SMEs generated."
- Do not set `onboarding_status: ready_for_questions`.
- Do not set `question_mode: enabled`.

If SME outputs exist but `sme-knowledge-map.md`, `knowledge-package-registry.md`, or `knowledge-packages/*/knowledge-pack.md` is missing:

- Say: "Using SME Knowledge Builder to generate knowledge packages."
- Use SME Knowledge Builder behavior automatically.
- Do not mark knowledge building complete while running.
- Set `knowledge_builder: complete` only after `knowledge-package-registry.md`, `sme-knowledge-map.md`, and at least one `knowledge-packages/*/knowledge-pack.md` file exist.
- Set `onboarding_status: knowledge_builder_complete` only after those Layer 4 artifacts exist.
- Say: "Knowledge packages generated."

If all Layer 1-4 outputs exist:

- Confirm these artifacts exist before changing state:
  - `shop-reference.md`
  - `sme-registry.md`
  - `sme-coverage.md`
  - at least one `smes/*.md` file
  - `knowledge-package-registry.md`
  - `sme-knowledge-map.md`
  - at least one `knowledge-packages/*/knowledge-pack.md` file
- Confirm `.shop-ai/state.md` records `shop_reference_status: finalized`.
- Confirm `.shop-ai/onboarding-log.md` does not contain unresolved ShopContext blocking questions.
- Confirm the finalization audit passes.
- Set `onboarding_status: ready_for_questions`.
- Set `question_mode: enabled`.
- Say: "ShopFloor AI is ready. You can now ask shop questions in plain English."

## Onboarding Log Rules

Update `.shop-ai/onboarding-log.md` incrementally after each completed stage, or write the final log only at the actual end of Layer 4.

The log must not claim future stages are complete before their output artifacts exist. If the log records timestamps, the final ready entry must correspond to the end of SME Knowledge Builder output creation, not the end of ShopContext.

## Question Mode

When `.shop-ai/state.md` says `onboarding_status: ready_for_questions` and `question_mode: enabled`, normal manufacturing shop questions should use SME Manager behavior by default, even if the user does not explicitly type `$sme-manager`.

The user-facing skill name is `$shopfloor-ai`.

Examples:

- What does Op 040 do?
- What is IM-110?
- What does this machine do?
- Explain this in layman's terms.
- What records should I ask the team to bring?
- The parts are shifting in the oven. What should I check?
- Is this before or after reflow?
- Which SME should I level up first?
- What happens if this press goes down?

Default answer style:

- concise
- plain language
- shop-aware
- no routing mechanics unless the user asks
- no debug output unless the user asks
- no root cause claims without evidence
- no corrective action recommendations without evidence and authority
- no accept/reject decisions without controlling criteria

Do not print setup status messages while answering normal ready-state shop questions.

## Required Boundaries

- Do not modify ShopContext, SME Generator, SME Manager, or SME Knowledge Builder behavior unless explicitly requested.
- Do not turn this wrapper into a second SME Manager.
- Do not reason directly from Layer 4 packages as the wrapper.
- SME Manager remains an orchestrator.
- Layer 4 packages attach to SMEs, not directly to the manager.
- Public or generic package knowledge cannot override shop-specific SME shell facts, user-uploaded documents, actual evidence, or controlling criteria.
- Do not make root cause, corrective action, production capacity, or accept/reject claims without evidence and authority.

## Reference Files

- `references/pipeline-state-contract.md`
- `references/onboarding-flow.md`
- `references/question-mode-routing.md`
- `references/status-messages.md`
