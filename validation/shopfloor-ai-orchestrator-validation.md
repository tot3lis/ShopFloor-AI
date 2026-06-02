# ShopFloor AI Orchestrator Validation

## Purpose

Validate the top-level `$shopfloor-ai` wrapper skill for the integrated manufacturing Layer 1-4 project.

## Files Created Or Updated

- `.agents/skills/shopfloor-ai/SKILL.md`
- `.agents/skills/shopfloor-ai/references/pipeline-state-contract.md`
- `.agents/skills/shopfloor-ai/references/onboarding-flow.md`
- `.agents/skills/shopfloor-ai/references/question-mode-routing.md`
- `.agents/skills/shopfloor-ai/references/status-messages.md`
- `AGENTS.md`
- `.shop-ai/state.template.md`
- `.shop-ai/onboarding-log.template.md`
- `README.md`

## Manual Validation Checklist

| Check | Result | Notes |
|---|---:|---|
| User-facing skill is now `shopfloor-ai` | pass | Skill metadata says `name: shopfloor-ai`; folder is `.agents/skills/shopfloor-ai/` |
| Old `step-automation` skill folder removed | pass | `.agents/skills/step-automation/` no longer exists |
| State contract exists | pass | `references/pipeline-state-contract.md` created under `shopfloor-ai` |
| Status message reference exists | pass | `references/status-messages.md` defines setup status behavior |
| Root `AGENTS.md` exists | pass | Repo-level ready-state and SME Manager instructions point to `$shopfloor-ai` |
| Chat-attached files are documented as primary onboarding path | pass | README, AGENTS, SKILL.md, and onboarding flow say users can drop messy files into Codex and run `$shopfloor-ai` |
| `inputs/` is optional | pass | Docs say `inputs/` may be used if preferred but is not required |
| `$shopfloor-ai` can start from user-provided files without a prebuilt `inputs/` folder | pass | Onboarding flow checks chat attachments and pasted prompt content before optional `inputs/` |
| Onboarding flow handles missing `shop-reference.md` | pass | `onboarding-flow.md` routes missing reference to ShopContext behavior |
| Onboarding flow blocks when no files are available | pass | If no chat attachments, pasted data, optional `inputs/` files, or existing `shop-reference.md` exist, it asks for routers, work orders, machine lists, operation exports, or shop notes |
| Onboarding flow stops for mandatory ShopContext questions | pass | State changes to `needs_shopcontext_answers`, prints the blocking status message, and asks only mandatory questions |
| Onboarding flow auto-runs SME Generator after finalized `shop-reference.md` | pass | `onboarding-flow.md` defines automatic SME generation when registry/shells are missing |
| Onboarding flow auto-runs SME Knowledge Builder after SME generation | pass | `onboarding-flow.md` defines automatic knowledge generation when registry/map are missing |
| Setup flow shows short status lines | pass | `status-messages.md` defines one-sentence status messages for ShopContext, SME Generator, SME Knowledge Builder, and ready state |
| Normal question mode does not show setup status lines | pass | `question-mode-routing.md` and `status-messages.md` prohibit setup status messages for normal ready-state shop questions |
| `ready_for_questions` state enables default SME Manager behavior | pass | `question-mode-routing.md` and `AGENTS.md` define this behavior |
| Normal shop questions no longer require explicit `$sme-manager` in intended MVP flow | pass | Ready-state routing defaults to SME Manager behavior |
| No normal shop question requires explicit `$sme-manager` after `ready_for_questions` | pass | Question mode routes normal manufacturing questions to SME Manager behavior by default |
| Manager remains orchestrator only | pass | `question-mode-routing.md` preserves manager orchestration boundary |
| Knowledge packages attach to SMEs, not directly to manager | pass | `question-mode-routing.md` and `AGENTS.md` state this boundary |
| `.shop-ai/` remains the state folder | pass | `pipeline-state-contract.md` explicitly preserves `.shop-ai/`; no `.shopfloor-ai/` folder was introduced |
| Old `step-automation` references removed or intentionally limited to historical validation notes | pass | Current public docs and active validation use `$shopfloor-ai`; no active skill references remain |

## Preferred Setup Status Messages

- `Using ShopContext to generate the shop reference file.`
- `Shop reference file created.`
- `Using SME Generator to generate shop SMEs.`
- `Shop SMEs generated.`
- `Using SME Knowledge Builder to generate knowledge packages.`
- `Knowledge packages generated.`
- `ShopFloor AI is ready. You can now ask shop questions in plain English.`

If ShopContext has mandatory questions:

- `ShopContext needs a few confirmations before setup can continue.`

Then ask only the mandatory questions.

## Current State Templates

`.shop-ai/` contains templates only for the public package:

- `.shop-ai/state.template.md`
- `.shop-ai/onboarding-log.template.md`

Local generated state files remain ignored:

- `.shop-ai/state.md`
- `.shop-ai/onboarding-log.md`

## Behavior Boundaries Confirmed

- Existing Layer 1-4 skills were not merged or rewritten.
- Routing logic inside SME Manager was not changed.
- Layer 4 package handling was not changed.
- Source priority was not changed.
- Root cause, corrective action, capacity estimates, and accept/reject decisions remain evidence-bound.

## Result

Pass.

The `$shopfloor-ai` skill now provides the intended MVP front door: onboarding messy inputs, showing short setup status lines, stopping for mandatory ShopContext questions, auto-running SME and knowledge generation when outputs are missing, and enabling normal shop questions through SME Manager behavior once ready.
