# SME Knowledge Map Template

Create `sme-knowledge-map.md` to attach packages to generated SMEs without editing the SME shell files.

```markdown
# SME Knowledge Map

## Purpose
This map connects generated SME shells to reusable Layer 4 knowledge packages. It does not modify SME scope, shop authority, or approval status.

## Source Inputs

| Input | Present | Notes |
|---|---:|---|
| sme-registry.md | <yes/no> | <notes> |
| smes/*.md | <count> | <notes> |
| shop-reference.md | <yes/no> | <notes> |
| user-uploaded documents | <yes/no> | <notes> |

## SME: <SME Name>

Role: <role from shell or registry>

Owned scope: <process/capability/equipment/material/inspection scope>

### Primary Packages

Packages directly owned by the SME's role/process/equipment scope.

| Package | Level | Why It Applies | Input Mapping Confidence | Technical Source Confidence | Boundaries |
|---|---|---|---|---|---|
| <package-name> | <general/process/equipment/model/material/inspection/etc.> | <input-derived reason> | <high/medium/low> | <high/medium/low/placeholder/not gathered> | <cautions> |

### Context Packages

Packages useful for cross-process interpretation, handoffs, inspection interactions, upstream/downstream effects, or adjacent SME reasoning.

Context packages do not expand SME ownership. They only provide background that helps the SME interpret issues involving other processes.

| Package | Level | Why It Helps Context | Input Mapping Confidence | Technical Source Confidence | Ownership Boundary |
|---|---|---|---|---|---|
| <package-name> | <general/process/equipment/model/material/inspection/etc.> | <handoff/cross-process reason> | <high/medium/low> | <high/medium/low/placeholder/not gathered> | <state that this does not expand SME ownership> |

### Missing Package Opportunities

- `<candidate-package>`: <why it may be useful, what source or input is missing>

### Boundaries And Cautions

- <limits from SME shell, registry, shop-reference, or source coverage>
```

Include every SME found in the inputs. If an SME has no safe primary or context package attachment, say so and explain what is missing. Do not place every package under one generic attached-package list.
