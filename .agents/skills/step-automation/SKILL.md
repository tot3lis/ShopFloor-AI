---
name: step-automation
description: Front-door orchestration skill for the manufacturing Layer 1-4 shop AI workflow. Use when onboarding messy shop inputs, maintaining .shop-ai/state.md, running ShopContext, SME Generator, and SME Knowledge Builder in order, or routing normal ready-state shop questions to SME Manager behavior by default.
---

# Step Automation

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

- messy files in `inputs/`
- user-uploaded files
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
2. Read or create `.shop-ai/state.md`.
3. Read `references/onboarding-flow.md`.
4. Inspect the project for generated outputs:
   - `shop-reference.md`
   - `sme-registry.md`
   - `smes/*.md`
   - `sme-knowledge-map.md`
   - `knowledge-package-registry.md`
5. If onboarding is incomplete, continue the pipeline in order.
6. If all required outputs exist, set:
   - `onboarding_status: ready_for_questions`
   - `question_mode: enabled`
7. For normal manufacturing shop questions while ready, follow `references/question-mode-routing.md` and answer using SME Manager behavior by default.

## Onboarding Behavior

If `shop-reference.md` does not exist:

- Use ShopContext behavior.
- Collect messy inputs from `inputs/` and/or user-provided files.
- If ShopContext has mandatory blocking questions, set `onboarding_status: needs_shopcontext_answers`, record the questions in `.shop-ai/onboarding-log.md`, ask only those mandatory questions, and stop.

If ShopContext mandatory questions have been answered:

- Use ShopContext behavior to finalize `shop-reference.md`.
- Set `shop_reference: finalized`.
- Set `onboarding_status: ready_for_generation`.

If `shop-reference.md` exists but `sme-registry.md` or `smes/*.md` is missing:

- Use SME Generator behavior automatically.
- Set `onboarding_status: generating_smes` while running.
- Set `sme_generation: complete` when outputs exist.

If SME outputs exist but `sme-knowledge-map.md` or `knowledge-package-registry.md` is missing:

- Use SME Knowledge Builder behavior automatically.
- Set `onboarding_status: generating_knowledge` while running.
- Set `knowledge_builder: complete` when outputs exist.

If all Layer 1-4 outputs exist:

- Set `onboarding_status: ready_for_questions`.
- Set `question_mode: enabled`.
- Tell the user they can now ask normal shop questions in plain English.

## Question Mode

When `.shop-ai/state.md` says `onboarding_status: ready_for_questions` and `question_mode: enabled`, normal manufacturing shop questions should use SME Manager behavior by default, even if the user does not explicitly type `$sme-manager`.

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
