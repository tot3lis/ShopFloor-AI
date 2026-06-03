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
| Explicit `shopfloor-ai` invocation beats ShopContext file matching | pass | `shopfloor-ai` metadata and AGENTS.md say `run shopfloor-ai`, `$shopfloor-ai`, and `use shopfloor-ai` route to the top-level orchestrator even when attached files look like ShopContext inputs |
| Old `step-automation` skill folder removed | pass | `.agents/skills/step-automation/` no longer exists |
| State contract exists | pass | `references/pipeline-state-contract.md` created under `shopfloor-ai` |
| Status message reference exists | pass | `references/status-messages.md` defines setup status behavior |
| Root `AGENTS.md` exists | pass | Repo-level ready-state and SME Manager instructions point to `$shopfloor-ai` |
| Chat-attached files are documented as primary onboarding path | pass | README, AGENTS, SKILL.md, and onboarding flow say users can drop messy files into Codex and run `$shopfloor-ai` |
| `inputs/` is optional | pass | Docs say `inputs/` may be used if preferred but is not required |
| `$shopfloor-ai` can start from user-provided files without a prebuilt `inputs/` folder | pass | Onboarding flow checks chat attachments and pasted prompt content before optional `inputs/` |
| Onboarding flow handles missing `shop-reference.md` | pass | `onboarding-flow.md` routes missing reference to ShopContext behavior |
| Onboarding flow blocks when no files are available | pass | If no chat attachments, pasted data, optional `inputs/` files, or existing `shop-reference.md` exist, it asks for routers, work orders, machine lists, operation exports, or shop notes |
| Onboarding flow stops for mandatory ShopContext questions | pass | State changes to `awaiting_shopcontext_confirmations`, `shop_reference_status: review_needed`, prints the blocking status message, and asks only mandatory questions |
| Onboarding flow auto-runs SME Generator after finalized `shop-reference.md` | pass | `onboarding-flow.md` defines automatic SME generation only when `shop_reference_status: finalized` and registry/shells are missing |
| Onboarding flow auto-runs SME Knowledge Builder after SME generation | pass | `onboarding-flow.md` defines automatic knowledge generation when registry/map are missing |
| Planning can read later-layer instructions before execution | pass | `SKILL.md`, `onboarding-flow.md`, and `pipeline-state-contract.md` allow later-layer skill/reference reads for planning and validation |
| Later-layer execution is gated by upstream artifacts and state | pass | SME Generator requires final `shop-reference.md`, `shop_reference_status: finalized`, and no unresolved ShopContext blocking questions; SME Knowledge Builder requires `sme-registry.md`, `sme-coverage.md`, and at least one `smes/*.md` file |
| Public-source Layer 4 gathering is treated as Layer 4 execution | pass | Contract states public-source research/gathering must not begin before SME outputs exist |
| State is not pre-written to final ready state | pass | Contract requires incremental state updates and forbids `ready_for_questions` until artifact checks pass |
| `ready_for_questions` requires full artifact and ShopContext finalization checks | pass | Required checks include `shop_reference_status: finalized`, Layer 1 file, SME registry/coverage/shells, knowledge registry/map, and at least one `knowledge-packages/*/knowledge-pack.md` |
| Onboarding log cannot claim future stages early | pass | Contract says the log updates incrementally or final-writes only after Layer 4 completes |
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

The state template includes `shop_reference_status`, which is the hard downstream gate for SME Generator.

Local generated state files remain ignored:

- `.shop-ai/state.md`
- `.shop-ai/onboarding-log.md`

## Behavior Boundaries Confirmed

- Existing Layer 1-4 skills were not merged or rewritten.
- Routing logic inside SME Manager was not changed.
- Layer 4 package handling was not changed.
- Source priority was not changed.
- Root cause, corrective action, capacity estimates, and accept/reject decisions remain evidence-bound.

## Gold-Test Routing / State Finding

A cold-test run showed that generated artifacts were produced in the correct order:

1. `shop-reference.md`
2. SME outputs
3. knowledge package outputs

However, `.shop-ai/state.md` and `.shop-ai/onboarding-log.md` were written at the same time as `shop-reference.md` and already claimed later stages and `ready_for_questions` were complete. That created a bad intermediate window where question mode could appear enabled before SME and knowledge artifacts existed.

New pass criteria:

- State must not be pre-written to final ready state.
- `shop-reference.md` existence must not be treated as ShopContext finalization.
- `shop_reference_status: finalized` is required before SME Generator can execute.
- `ShopContext Review - User Confirmation Needed`, `ShopContext Review - Still Blocked`, or `Blocking Open Questions` must block all downstream layers.
- `ready_for_questions` requires explicit artifact existence checks.
- SME Knowledge Builder and public-source Layer 4 gathering must not begin before SME outputs exist.
- Reading later-layer instructions for planning is allowed and is not treated as layer execution.
- Onboarding log entries must not claim future stages are complete before the stage artifacts exist.

## Required Regression Case: ShopContext review gate blocks downstream layers

### Test Setup

Run `$shopfloor-ai` from a clean repo state with messy inputs that intentionally contain unresolved operation/machine/work-center ambiguity. The inputs should make ShopContext produce one of its review-gate signals:

- `ShopContext Review - User Confirmation Needed`
- `ShopContext Review - Still Blocked`
- `Blocking Open Questions`

### Expected Behavior

- ShopFloor AI runs ShopContext.
- ShopFloor AI stops immediately at the ShopContext review gate.
- User-facing output says:

  `ShopContext needs a few confirmations before setup can continue.`

- Only the blocking questions are shown by default.
- No SME files are generated:
  - no `sme-registry.md`
  - no `sme-coverage.md`
  - no `smes/`
- No knowledge files are generated:
  - no `knowledge-package-registry.md`
  - no `sme-knowledge-map.md`
  - no `knowledge-packages/`
- `.shop-ai/state.md` records:
  - `onboarding_status: awaiting_shopcontext_confirmations`
  - `shop_reference_status: review_needed`
  - `question_mode: disabled`
- `.shop-ai/state.md` does not say `ready_for_questions`.
- `.shop-ai/onboarding-log.md` records the blocking ShopContext questions.
- After the user answers those questions, the next run uses ShopContext behavior to finalize `shop-reference.md`, writes `shop_reference_status: finalized`, and only then continues to SME Generator and SME Knowledge Builder.

### Cold-Test Prompt

Use:

```text
run shopfloor-ai
```

Attach or paste an ambiguous router, machine list, and shop notes where at least one normal operation has conflicting machine/work-center ownership or a generic operation name that affects downstream mapping. The expected first-run result is the blocking status message and no downstream artifacts.

## Required Regression Case: Explicit shopfloor-ai invocation wins over ShopContext file matching

### Input

```text
attached router-export.md
attached machine-list.md
prompt: run shopfloor-ai
```

### Expected

- Codex invokes `shopfloor-ai` as the top-level orchestrator.
- `shopfloor-ai` uses ShopContext internally.
- Codex does not say it is choosing `shop-context` instead of `shopfloor-ai`.

## Result

Pass.

The `$shopfloor-ai` skill now provides the intended MVP front door: onboarding messy inputs, showing short setup status lines, stopping for mandatory ShopContext questions, auto-running SME and knowledge generation when outputs are missing, updating state incrementally, and enabling normal shop questions through SME Manager behavior only after ready-state artifact checks pass.
