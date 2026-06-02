# Shop Reference Schema

`shop-reference.md` is the final output of ShopContext. It is a lean, AI-readable manufacturing context file for one shop, shop area, line, cell, or process family.

The final reference should explain how the shop appears to work based on the provided documents. It should preserve exact shop language while normalizing meanings for AI use.

Do not invent missing shop facts. Final `shop-reference.md` may only contain non-blocking unknowns. Blocking unknowns stop finalization and require user review before final output.

## Scope Boundary

`shop-reference.md` describes shop context only.

It should not include:

- Defect investigations
- Root cause claims
- Corrective actions
- Historical defect trend analysis
- SPC analysis
- Machine performance analysis
- Maintenance event analysis
- Dynamic MES, QMS, ERP, or data integration

If defect, maintenance, quality, or records data appears in the source material, only include it when it helps define the shop context. Do not analyze it.

## Lean Final Structure

The final `shop-reference.md` must use this structure:

# Shop Reference

## 1. Shop Type / Process Context

Plain-language summary of what the shop appears to build or process, the manufacturing style, and major process families. Include only source-supported or clearly labeled inferred context.

Do not include a separate source-document inventory unless the user asks for it. Source review belongs in the ShopContext Review stage.

## 2. Standard Operation Flow

Ordered flow of operations. Preserve source order and operation numbers exactly.

If multiple product flows differ, show common flow plus product-specific branches instead of flattening all products into one universal route.

Router operations are process containers, not necessarily atomic steps. If an operation instruction shows many internal steps inside one operation, keep the operation as one router operation in the flow and summarize its internal steps in `## 4. Operation Step Summaries`.

## 3. Operation Dictionary

For each operation, include:

- Operation number exactly as shown
- Operation name exactly as shown
- Work center exactly as shown
- Plain-English meaning
- Product, route, or family where it appears when known
- Notes only when needed to preserve context

Avoid confidence clutter in the final reference. Use `appears to`, `likely`, or `Unknown` only for non-blocking unknowns. Blocking unknowns stop finalization.

## 4. Operation Step Summaries

This is the main place for the real work content.

For each operation or operation family, summarize:

- Internal process steps from attached operation instructions
- Machines, equipment, fixtures, benches, stations, or tools used
- Manual or human-judgment work
- Inspection, test, review, acceptance, or other quality gates inside the operation
- Key parameters explicitly stated in the source, such as temperatures, times, materials, programs, fixtures, or acceptance language
- Confirmed Records / Logs, only when the source explicitly confirms that the shop retains or uses those records/logs/forms/results

Do not copy the full instruction text into `shop-reference.md`.

Do not include generic likely records such as machine logs, operator notes, inspection records, photos, test results, or setup sheets unless the source explicitly confirms them.

## 5. Work Center Dictionary

For each work center, describe what kind of work it appears to perform.

For numeric or coded work centers:

- Preserve the raw work center exactly.
- Keep any plain-English description in a separate `Inferred Meaning` or equivalent field.
- Do not rename numeric work centers as facts.

Include associated operations and major machines/equipment only when source-supported or clearly inferred.

## 6. Machine / Equipment Dictionary

List machines, equipment, fixtures, benches, lines, cells, stations, tools, and asset IDs found in the sources.

For each item, include:

- Name exactly as shown
- Type or capability when known
- Work center exactly as shown, or `Unknown`
- Associated operation or process when supported
- Notes for ambiguous, backup, inactive, shared, or unmapped equipment

Machine-to-operation mapping should be concise here and expanded only where needed in `## 4. Operation Step Summaries`.

## 7. Quality Gates

List inspection, test, review, verification, acceptance, disposition, and approval points.

For each quality gate, include:

- Operation number and name
- Gate type
- What appears to be checked or decided
- Machine/equipment/station if known
- Product or route scope if known

Do not turn every operation into a quality gate. Include only operations or internal steps that are explicitly inspection/test/review/acceptance-related or clearly quality-control points.

## 8. Shop-Specific Language

Combine terminology and ambiguity handling here.

Include:

- Shop acronyms
- Alternate names for the same process
- Overloaded terms with multiple meanings
- Terms that require operation context to interpret
- Internal labels, machine nicknames, work center names, product family names, and process names found in the sources

Preserve original terms while explaining normalized meaning.

## Removed From Final Reference

Do not include these as standalone final sections:

- Source Documents Reviewed
- Product Families
- Machine-To-Operation Map
- Manual / Human Operations
- Inspection And Test Points
- Likely Evidence Sources By Operation
- Open Mapping Questions
- Revision Notes

These topics may appear only when folded into the lean sections above, and only where they add useful shop context.
