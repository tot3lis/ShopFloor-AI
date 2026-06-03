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

In practice, ShopFloor AI first builds the shop brain, then turns on the shop assistant. The setup execution order is: `shop-reference.md` -> SME shells -> SME knowledge packs -> SME Manager question mode.

## How It Works

ShopFloor AI runs setup automatically after the user uploads files and types `run shopfloor-ai`. Users do not manually run each piece.

### Build The Shop Reference

ShopFloor AI builds `shop-reference.md`. This turns messy shop data into a structured map of products, operations, work centers, machines, inspection gates, shop language, and known uncertainty.

`shop-reference.md` must be finalized before SMEs are generated. If ShopContext finds blocking uncertainty, setup pauses and asks only the needed questions. It will not generate SMEs or knowledge packs until the shop reference is finalized.

### Generate Shop SMEs

ShopFloor AI reads the finalized reference and generates shop-aware machine, process, inspection, and flow experts:

- `sme-registry.md`
- `sme-coverage.md`
- `smes/*.md`

These SME shells define which experts the assistant can route questions to.

### Build SME Knowledge Packs

ShopFloor AI builds knowledge packs for the generated SMEs:

- `knowledge-package-registry.md`
- `sme-knowledge-map.md`
- `knowledge-packages/*`

Knowledge packs give the generated SMEs broader technical context while staying bounded by shop-specific facts. They do not override shop facts, uploaded documents, actual evidence, or controlling acceptance criteria.

### Turn On Question Mode

After the reference, SMEs, and knowledge packs exist, ShopFloor AI turns on question mode. SME Manager becomes the front door for user questions.

SME Manager:

- routes each question to the right generated SMEs
- lets selected SMEs use their shop facts and linked knowledge packs
- combines the SME responses into one practical answer for the user

The setup order is: `shop-reference.md` -> SME shells -> SME knowledge packs -> SME Manager question mode.

Question mode is not enabled until the reference, SMEs, and knowledge packs exist.

## Quick Start

1. Clone this repo.
2. Open the repo in Codex.
3. Drop/upload shop files into the chat.
4. Type:

   ```text
   run shopfloor-ai
   ```

5. Answer any setup questions.
6. When it says ready, ask shop questions in plain English.

Do not run the lower-level skills directly for normal onboarding. ShopFloor AI will run them in order.

You may also place files in `inputs/` if you prefer a folder-based workflow, but `inputs/` is optional. The easiest MVP path is to attach or paste the files in Codex and run `$shopfloor-ai`.

## What To Upload

The best starting point is usually:

- a router export or operation export with operation numbers, operation names, work centers, and product or part family context
- a machine/equipment list with machine names, aliases if available, work centers if available, and what each machine is used for

Other shop files can also help, especially when they add context to the operation flow or machine mappings. Supporting files may include work orders, travelers, inspection/test station lists, asset exports, selected work instruction excerpts, and short notes that clarify ambiguous operation, work center, or machine mappings.

Notes alone may not be enough to build a reliable shop reference if they do not explain the operation flow or machine/equipment context.

Good starting package example:

- router or operation export
- machine/equipment list
- optional short notes explaining unclear operation, work center, or machine mappings

Best file types:

- `.csv`
- `.xlsx`
- `.md`
- `.txt`
- text-readable `.pdf`

Not ideal:

- screenshots
- scanned PDFs
- image-only files

Illustrative example notes:

These examples are documentation only. ShopFloor AI must not treat them as shop facts or use them to resolve ambiguity in attached, pasted, or `inputs/` files.

- Op 030 Place Components can run on MY200 SX or MY300 DX depending on program availability.
- Work center 635C01 is Koh Young AOI for CCA-PWR.
- Final verify is manual microscope review.
- GenRad Test Rack 2 retains test records for CCA-CTRL only.

## Example Questions

- What does Op 040 do?
- What is IM-110 and what does it do?
- What records should I ask the team to bring?
- The parts are shifting in the oven. What should I check?
- Which SME should I level up first?

## Files And Outputs

- `.agents/skills/` contains the Codex skills.
- `examples/` contains synthetic examples.
- Generated shop outputs are local and ignored by git.

## Limitations

- ShopFloor AI does not replace quality authority, engineering authority, approved work instructions, customer requirements, or acceptance criteria.
- It should not claim root cause, corrective action, accept/reject decisions, or exact production impact without evidence.
- Public/generic knowledge packs are background context, not shop-approved truth.
- Output quality depends on the quality of the router/operation export and machine/equipment list.

## License

MIT License. See `LICENSE`.
