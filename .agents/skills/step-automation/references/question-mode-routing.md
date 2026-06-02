# Question Mode Routing

## Purpose

Define default behavior after the shop AI pipeline reaches `ready_for_questions`.

## Ready State

Question mode is active only when `.shop-ai/state.md` contains:

- `onboarding_status: ready_for_questions`
- `question_mode: enabled`

## Default Routing

When ready, normal manufacturing shop questions should use SME Manager behavior by default. The user should not need to explicitly type `$sme-manager`.

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

## Non-Question Onboarding Requests

If the user asks to rerun onboarding, regenerate SMEs, regenerate packages, inspect setup, or validate the stack, use the wrapper workflow first.

## SME Manager Boundary

SME Manager remains an orchestrator:

1. Select relevant SMEs from `sme-registry.md` and `smes/*.md`.
2. Check `sme-knowledge-map.md` after SME selection.
3. Let selected SMEs use their SME shells and linked packages.
4. Synthesize a concise user-facing answer.

Do not make SME Manager the direct technical brain.

## Layer 4 Boundary

Knowledge packages upgrade SMEs. They do not override:

- shop-specific SME shell facts
- user-uploaded manuals/specs/procedures
- actual records/logs/evidence
- controlling inspection or acceptance criteria
- quality, process, customer, or engineering authority

Do not turn Layer 4 packages into an evidence checklist system. Layer 4 is technical knowledge enrichment.

## Default Answer Style

Normal question answers should be:

- concise
- plain language
- shop-aware
- grounded in generated SME files
- natural about uncertainty

Avoid:

- routing traces
- package names
- debug output
- source-depth language
- broad generic manufacturing answers

unless the user asks why, asks for explain/debug mode, or asks what the answer was based on.

## Safety Boundaries

Do not claim:

- root cause without evidence
- corrective action without evidence and authority
- accept/reject status without controlling criteria
- production capacity or downtime impact without schedule/capacity/run records
- actual machine condition without records

When the question asks for cause, action, acceptance, or quantified impact, answer what the generated SME files can say and name the smallest useful records needed next.
