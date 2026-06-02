# ShopFloor AI

ShopFloor AI is a layered manufacturing AI stack that turns messy shop data into a shop-aware assistant. It builds shop context, generates machine/process SMEs, enriches them with knowledge packs, and lets users ask practical shop questions in plain English.

## What It Does

ShopFloor AI helps teams turn scattered manufacturing information into a structured, shop-aware question-answering workflow.

It can:

- read messy shop inputs such as chat-attached routers, work orders, machine lists, work-center exports, operation notes, and user corrections
- create a shop reference from those inputs
- generate machine, process, inspection, and flow SME shells
- enrich SMEs with reusable technical knowledge packs
- answer practical manufacturing questions in plain English

## Why It Exists

Most shop knowledge is not stored in one clean system. It lives across routers, spreadsheets, tribal notes, machine names, operation numbers, work centers, and inspection practices.

ShopFloor AI provides a layered way to organize that knowledge without pretending generic AI knows your shop. The system first builds shop-specific context, then generates SMEs, then enriches those SMEs with bounded technical knowledge.

## Layered Architecture

### Layer 1: ShopContext

Creates `shop-reference.md` from messy manufacturing shop data. It maps products, operations, work centers, machines, inspection gates, conditional steps, and uncertainty.

### Layer 2: SME Generator

Reads `shop-reference.md` and generates:

- `sme-coverage.md`
- `sme-registry.md`
- `smes/*.md`

These SME shells define which machine, process, inspection, or flow experts the shop assistant can route questions to.

### Layer 3: SME Manager

Routes shop questions to the relevant SMEs, gathers SME contributions, and synthesizes concise user-facing answers.

The manager remains an orchestrator. It does not become the technical knowledge base directly.

### Layer 4: SME Knowledge Builder / Knowledge Packs

Builds reusable knowledge packages and maps them to SMEs:

- `knowledge-package-registry.md`
- `sme-knowledge-map.md`
- `knowledge-packages/*/knowledge-pack.md`
- `knowledge-packages/*/source-map.md`

Knowledge packs upgrade SMEs. They do not override shop-specific facts.

### Layer 5: Future Uploaded Evidence

Future workflows can incorporate user-uploaded manuals, work instructions, specs, inspection plans, calibration records, travelers, logs, and actual production evidence.

## Quick Start

1. Clone this repo.
2. Open the repo in Codex.
3. Drop messy shop files directly into the Codex chat.
4. Type: `run shopfloor-ai`.
5. Answer any mandatory ShopContext questions.
6. Wait for SME Generator and SME Knowledge Builder to run automatically.
7. Once `ready_for_questions` is enabled, ask normal shop questions in plain English.

You may also place files in `inputs/` if you prefer a folder-based workflow, but `inputs/` is optional. The easiest MVP path is to attach or paste the files in Codex and run `$shopfloor-ai`.

## Example Questions

- What does Op 040 do?
- What is IM-110 and what does it do?
- What records should I ask the team to bring?
- The parts are shifting in the oven. What should I check?
- Which SME should I level up first?

## Repository Structure

```text
.agents/
  skills/
    shop-context/
    sme-generator/
    sme-manager/
    sme-knowledge-builder/
    shopfloor-ai/
.shop-ai/
  state.template.md
  onboarding-log.template.md
examples/
  synthetic-injection-molding-shop/
    README.md
    outputs/
validation/
  shopfloor-ai-orchestrator-validation.md
AGENTS.md
LICENSE
README.md
```

Generated local shop outputs are intentionally ignored at the package root:

- `shop-reference.md`
- `sme-registry.md`
- `sme-coverage.md`
- `smes/`
- `sme-knowledge-map.md`
- `knowledge-package-registry.md`
- `knowledge-packages/`
- `.shop-ai/state.md`
- `.shop-ai/onboarding-log.md`

## Source Priority And Safety Boundaries

ShopFloor AI is designed to respect source authority.

Source priority should generally move from strongest to weakest:

1. user-uploaded manuals, procedures, specs, criteria, and records
2. generated shop-specific SME shells and shop context
3. linked knowledge packages
4. public or generic manufacturing knowledge

Public or generic knowledge packages must not override shop-specific facts, user-uploaded documents, actual evidence, or controlling acceptance criteria.

## Limitations

ShopFloor AI does not replace:

- quality authority
- engineering authority
- approved work instructions
- customer specifications
- acceptance criteria
- qualified manufacturing judgment

It does not:

- make accept/reject decisions without controlling criteria
- claim root cause without evidence
- recommend corrective action without evidence and authority
- treat public knowledge as shop-approved truth
- quantify production impact without schedule, capacity, or run records

## Synthetic Example

The `examples/synthetic-injection-molding-shop/` folder contains fully synthetic generated outputs. They are included only to show what the system can produce.

Do not edit the example to onboard your own shop. Drop messy shop files into Codex, or place them in `inputs/` if you prefer a folder-based workflow.

## Validation Status

Current validation artifacts include:

- `validation/shopfloor-ai-orchestrator-validation.md`
- `validation/public-package-cleanup-validation.md`

The public package validation confirms that root-level live generated outputs are excluded, `.shop-ai/` contains templates only, all five skills are present, and generated synthetic outputs are retained only under `examples/`.

## License

MIT License. See `LICENSE`.
