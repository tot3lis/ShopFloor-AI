# Knowledge Package Template

Create `knowledge-packages/<package-name>/knowledge-pack.md` with this structure. Keep content specific to the package scope and source coverage.

```markdown
# Knowledge Package: <Name>

## Package Purpose
Explain what this package helps the SME understand.

## Applies To
List SMEs, machines, capabilities, processes, product families, materials, or inspection/test methods this package supports.

## Knowledge Level
State whether this is:
- General manufacturing principle
- Process-family knowledge
- Process-subtype knowledge
- Equipment-family knowledge
- Machine/model-specific knowledge
- Material-specific knowledge
- Shop-specific uploaded-document knowledge
- Actual-record/log-based knowledge

Also state:

- Input Mapping Confidence
- Technical Source Confidence
- Source tier coverage

## Process Overview
Plain-language explanation of the process or capability.

## Core Principles
Explain the underlying engineering/manufacturing principles.

Tie each principle to the package scope. Where possible, mention the source tier or source family supporting the principle without turning the section into a bibliography.

## Equipment / Tooling / System Principles
Explain how the relevant equipment, tooling, fixtures, software, controls, inspection systems, or work cells generally function.

## Machine-Specific Notes
Include only when the input files name a machine/model and reliable public or uploaded sources support the detail.
If machine-specific support is weak, say so clearly.

Separate:

- exact machine/model facts supported by Tier 1/OEM or uploaded sources
- equipment-family facts that are not model-specific
- shop-specific generated facts from SME shells

## Key Process Variables
Include variables such as temperature, pressure, force, speed, time, flow, feed, rate, alignment, tolerance, material condition, surface condition, chemistry, tooling, fixturing, software settings, operator interaction, environmental conditions, and measurement method as applicable.
Do not include irrelevant variables just to fill the section.

For each variable, explain why it matters directionally. Do not provide numeric settings unless a source supports them and they are clearly not shop-approved.

## Process Window Concepts
Explain how engineers think about margins, operating ranges, limits, tradeoffs, and sensitivity.

## Materials, Parts, Geometry, And Environment Interactions
Explain how materials, geometry, tolerances, forces, temperature, pressure, motion, tooling, fixturing, fluids, chemistry, consumables, operators, software settings, and environment interact with the process as applicable.

## Common Failure Modes
List common issues associated with the process or equipment.
Keep them generic unless the source supports more specificity.

For each failure mode, keep the wording as "can be associated with" or "may contribute to" unless actual evidence exists.

## Failure Mechanisms
Explain why those failures happen physically, procedurally, mechanically, chemically, thermally, electrically, dimensionally, or operationally as applicable.

Connect mechanisms to variables and source support. Do not jump from mechanism to root cause.

## Practical Heuristics
Include rules of thumb and experienced-engineer thinking.
Label anecdotal or weakly sourced heuristics clearly.

Prefer bounded heuristics that help SMEs form questions or interpret patterns. Do not write mandatory evidence checklists.

## Troubleshooting Logic
Explain how an experienced SME thinks through symptoms without jumping to root cause.
This is reasoning logic, not a mandatory evidence checklist.

Use "consider", "compare", "separate", and "check consistency" language. Avoid prescriptive "must" language unless supported by a controlling source.

## Important Terminology
Define key terms.

## What This Package Can Help With
Explain what types of SME answers this package strengthens.

## What This Package Cannot Prove
Explain boundaries:
- cannot prove actual shop settings
- cannot prove approved recipes
- cannot prove customer acceptance criteria
- cannot prove actual root cause
- cannot prove final corrective action
- cannot replace machine manuals, work instructions, specs, drawings, quality authority, or build records

## Source Map
Summarize source coverage, state the package-level Technical Source Confidence, and link to source-map.md. If public sources were not actually gathered, say that technical source confidence is placeholder, not gathered, or low.

Include:

- strongest source tier
- weakest or missing source area
- whether source support is process-family, equipment-family, machine-model, shop-specific, uploaded-document, or actual-record based
```

If a section is not applicable, keep the heading and state why briefly. Do not add filler variables, failure modes, or equipment notes outside the package scope.
