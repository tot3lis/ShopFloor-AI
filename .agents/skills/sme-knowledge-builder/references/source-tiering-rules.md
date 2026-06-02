# Source Tiering Rules

Use a generic manufacturing-wide tier system. Do not create domain-specific tier rules.

## Tiers

- Tier 1: OEM manuals, OEM datasheets, OEM service notes, OEM application notes
- Tier 2: Standards bodies, industry standards, regulatory or quality references, accepted technical handbooks
- Tier 3: Material supplier docs, tooling supplier docs, equipment vendor application notes, process engineering guides
- Tier 4: Academic papers, conference papers, textbooks, university engineering references
- Tier 5: Reputable trade publications, manufacturing blogs, distributor technical pages, integrator guides
- Tier 6: Forums, Reddit, YouTube, anecdotal tricks, practitioner posts

Tier 6 can inform practical heuristics only when labeled anecdotal. Do not use Tier 6 as proof of shop practice, acceptance criteria, root cause, or required action.

## Current v0.1 Priority

1. Generated SME shell
2. `sme-registry.md`
3. `shop-reference.md`, if present
4. Public OEM or general knowledge
5. Anecdotal public knowledge, only when labeled

Generated files define SME scope. Public sources can enrich general knowledge. They do not approve procedures for the shop.

Separate input mapping confidence from technical source confidence. Generated SME shells, `sme-registry.md`, and `shop-reference.md` can support high Input Mapping Confidence, but they do not by themselves create medium/high Technical Source Confidence for technical claims.

If public sources were not actually gathered, Technical Source Confidence must be `placeholder`, `not gathered`, or `low`. Do not allow a package to imply medium/high technical source confidence when technical sources are only placeholders.

## Public Source Research Strategy

Run targeted searches after package candidates are derived. Search from most specific to most general:

1. Exact machine/model package:
   - `"<machine name>" manual`
   - `"<machine name>" datasheet`
   - `"<machine name>" specifications`
   - `site:<OEM domain> "<model>"`
2. Equipment-family package:
   - `"<equipment family>" principles`
   - `"<equipment family>" application guide`
   - `"<equipment family>" troubleshooting guide`
   - `"<equipment family>" metrology/processing/maintenance basics`
3. Process-family or subtype package:
   - `"<process>" principles`
   - `"<process>" processing guide`
   - `"<process>" common defects causes`
   - `"<process>" design/process guide`
4. Material-family package:
   - `"<material>" processing guide`
   - `"<material>" drying guide`
   - `"<material>" supplier processing recommendations`
5. Inspection/test-method package:
   - `"<method>" metrology principles`
   - `"<method>" measurement uncertainty`
   - `"<method>" calibration guide`
   - `"<method>" best practices`

Prefer sources in this order:

1. OEM/manufacturer manuals, datasheets, service notes, application notes.
2. Standards bodies, NIST or equivalent national metrology bodies, industry standards, accepted handbooks.
3. Material suppliers, tooling suppliers, equipment vendors, process engineering guides.
4. University/textbook/academic engineering references.
5. Reputable trade publications and integrator guides.
6. Anecdotal sources only for labeled practical heuristics.

For each package, aim for:

- at least one source for process/equipment principles
- one source for important variables or controls when available
- one source for common failure modes or mechanisms when available
- model-specific source only when making model-specific claims

If fewer than two credible public/uploaded sources are found for a package, keep Technical Source Confidence low unless one Tier 1-2 source directly covers the package scope.

Use official source pages directly when possible. Do not cite search results as sources.

## Future Layer 5 Priority

Document future upgrade opportunities with this priority:

1. Actual build evidence/logs
2. User-uploaded shop documents
3. User-uploaded machine manuals/specs
4. Generated `shop-reference.md` and SME shells
5. Public/OEM/general knowledge packages
6. Anecdotal tricks/forums/videos

Do not implement full Layer 5 behavior in v0.1 unless the user explicitly asks.

## Source Map Fields

Each `source-map.md` must include:

- Source title/name
- Source type
- Source tier
- URL or file reference when available
- What information came from the source
- Source confidence for that source
- Limitations
- Whether the source is a generated SME shell, `sme-registry.md`, `shop-reference.md`, public source actually gathered, public-source placeholder, user-uploaded document, or actual record/log
- Which package sections the source supports, such as principles, equipment behavior, variables, failure modes, terminology, or limitations

A public-source placeholder may support package scaffolding, but it does not substantiate technical claims as real cited evidence.

Use this structure:

```markdown
# Source Map: <Package Name>

## Source Coverage Summary
<Brief summary of what is well supported, partially supported, and unsupported.>

## Sources

| Source | Type | Tier | Location | Information Used | Source Confidence | Limitations | Source Basis |
|---|---|---|---|---|---|---|---|
| <title/name> | <OEM/manual/standard/generated shell/etc.> | <tier or generated-input> | <URL/file/path> | <claim support> | <high/medium/low/placeholder/not gathered> | <limits> | <generated SME shell/sme-registry.md/shop-reference.md/public source actually gathered/public-source placeholder/user-uploaded document/actual record/log> |

## Unsupported Or Deferred Claims

- <claim or topic>: <why it is not supported yet>
```

Add a short `## Research Queries Used` section before `## Unsupported Or Deferred Claims` when public search was performed.

## Claim Discipline

Use sources to support the level they actually cover:

- Machine-specific claims require machine-specific sources.
- Equipment-family claims may use OEM, vendor, handbook, or engineering guide sources for that family.
- Process-family claims may use standards, handbooks, textbooks, vendor guides, or reputable technical references.
- Shop-specific claims require user-provided shop documents, generated shop context, or actual records.
- Actual settings, recipes, acceptance criteria, and dispositions require shop authority or records.

## Technical Source Confidence Guidance

- `High`: package is supported by direct Tier 1-2 or uploaded/actual technical sources covering the specific process, method, equipment family, or machine model.
- `Medium`: package is supported by credible Tier 3-5 sources and the claims stay general rather than shop-approved or model-specific.
- `Low`: sources are sparse, indirect, partial, or cover only adjacent concepts.
- `Placeholder`: no real technical source was gathered, or all sources are only planned placeholders.
- `Not gathered`: source gathering was intentionally not performed or was blocked.

Never use high Technical Source Confidence for generated SME shells alone.
