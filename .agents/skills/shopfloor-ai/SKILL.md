---
name: shopfloor-ai
description: Front-door orchestration skill for the ShopFloor AI manufacturing Layer 1-4 workflow. Use when onboarding messy shop inputs, maintaining .shop-ai/state.md, running ShopContext, SME Generator, and SME Knowledge Builder in order, or routing normal ready-state shop questions to SME Manager behavior by default.
---

# ShopFloor AI

## Purpose

Act as the top-level wrapper for the integrated manufacturing shop AI workflow.

This skill does not replace, merge, or rewrite the Layer 1-4 skills. It coordinates them in order:

1. ShopContext creates or finalizes `shop-reference.md` from messy shop inputs.
2. SME Generator creates `sme-coverage.md`, `sme-registry.md`, and `smes/*.md`.
3. SME Knowledge Builder creates `knowledge-package-registry.md`, `sme-knowledge-map.md`, and `knowledge-packages/*`.
4. SME Manager answers normal shop questions after the project is ready.

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
6. If onboarding is incomplete, continue the pipeline in order and show short setup status messages from `references/status-messages.md`.
7. If all required outputs exist, set:
   - `onboarding_status: ready_for_questions`
   - `question_mode: enabled`
8. For normal manufacturing shop questions while ready, follow `references/question-mode-routing.md` and answer using SME Manager behavior by default. Do not show pipeline setup status messages for normal questions.

## Planning Vs Execution Boundary

The wrapper may read later-layer skill files and reference files while planning the workflow, checking contracts, or understanding the required sequence.

Reading instructions is not execution.

Do not execute a layer until its required input artifacts exist:

- Do not run SME Generator until `shop-reference.md` exists, is finalized, and mandatory ShopContext questions are resolved.
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
- If ShopContext has mandatory blocking questions, say: "ShopContext needs a few confirmations before setup can continue."
- Set `onboarding_status: needs_shopcontext_answers`, record the questions in `.shop-ai/onboarding-log.md`, ask only those mandatory questions, and stop.
- When the file is created/finalized, say: "Shop reference file created."

If ShopContext mandatory questions have been answered:

- Use ShopContext behavior to apply the answers.
- Finalize `shop-reference.md`.
- Record the answers in `.shop-ai/onboarding-log.md`.
- Set `shop_reference: finalized`.
- Set `onboarding_status: ready_for_generation`.
- Do not set `onboarding_status: ready_for_questions`.
- Do not set `question_mode: enabled`.

If `shop-reference.md` exists and is finalized but `sme-registry.md`, `sme-coverage.md`, or `smes/*.md` is missing:

- Say: "Using SME Generator to generate shop SMEs."
- Use SME Generator behavior automatically.
- Set `onboarding_status: generating_smes` while running.
- Set `sme_generation: complete` only after `sme-registry.md`, `sme-coverage.md`, and at least one `smes/*.md` shell exist.
- Say: "Shop SMEs generated."
- Do not set `onboarding_status: ready_for_questions`.
- Do not set `question_mode: enabled`.

If SME outputs exist but `sme-knowledge-map.md`, `knowledge-package-registry.md`, or `knowledge-packages/*/knowledge-pack.md` is missing:

- Say: "Using SME Knowledge Builder to generate knowledge packages."
- Use SME Knowledge Builder behavior automatically.
- Set `onboarding_status: generating_knowledge` while running.
- Set `knowledge_builder: complete` only after `knowledge-package-registry.md`, `sme-knowledge-map.md`, and at least one `knowledge-packages/*/knowledge-pack.md` file exist.
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
