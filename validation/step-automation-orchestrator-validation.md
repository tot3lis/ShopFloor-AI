# Step Automation Orchestrator Validation

## Purpose

Validate the new top-level `step-automation` wrapper skill for the integrated manufacturing Layer 1-4 project.

## Files Created

- `.agents/skills/step-automation/SKILL.md`
- `.agents/skills/step-automation/references/pipeline-state-contract.md`
- `.agents/skills/step-automation/references/onboarding-flow.md`
- `.agents/skills/step-automation/references/question-mode-routing.md`
- `AGENTS.md`
- `.shop-ai/state.md`
- `.shop-ai/onboarding-log.md`

## Files Updated

- `README.md`

## Manual Validation Checklist

| Check | Result | Notes |
|---|---:|---|
| Wrapper skill exists | pass | `.agents/skills/step-automation/SKILL.md` created |
| State contract exists | pass | `references/pipeline-state-contract.md` created |
| Root `AGENTS.md` exists | pass | Repo-level ready-state and SME Manager instructions added |
| Onboarding flow handles missing `shop-reference.md` | pass | `onboarding-flow.md` routes missing reference to ShopContext behavior |
| Onboarding flow stops for mandatory ShopContext questions | pass | State changes to `needs_shopcontext_answers` and asks only mandatory questions |
| Onboarding flow auto-runs SME Generator after finalized `shop-reference.md` | pass | `onboarding-flow.md` defines automatic SME generation when registry/shells are missing |
| Onboarding flow auto-runs SME Knowledge Builder after SME generation | pass | `onboarding-flow.md` defines automatic knowledge generation when registry/map are missing |
| `ready_for_questions` state enables default SME Manager behavior | pass | `question-mode-routing.md` and `AGENTS.md` define this behavior |
| Normal shop questions no longer require explicit `$sme-manager` in intended MVP flow | pass | Ready-state routing defaults to SME Manager behavior |
| Manager remains orchestrator only | pass | `question-mode-routing.md` preserves manager orchestration boundary |
| Knowledge packages attach to SMEs, not directly to manager | pass | `question-mode-routing.md` and `AGENTS.md` state this boundary |

## Current State File

`.shop-ai/state.md` is initialized to:

- `onboarding_status: ready_for_questions`
- `shop_reference: finalized`
- `sme_generation: complete`
- `knowledge_builder: complete`
- `question_mode: enabled`

This matches the current integration project because Layer 1-4 outputs already exist.

## Behavior Boundaries Confirmed

- Existing Layer 1-4 skills were not merged or rewritten.
- Routing logic inside SME Manager was not changed.
- Layer 4 package handling was not changed.
- Source priority was not changed.
- Root cause, corrective action, capacity estimates, and accept/reject decisions remain evidence-bound.

## Result

Pass.

The `step-automation` skill now provides the intended MVP front door: onboarding messy inputs, stopping for mandatory ShopContext questions, auto-running SME and knowledge generation when outputs are missing, and enabling normal shop questions through SME Manager behavior once ready.
