# Registry Template

Create `knowledge-package-registry.md` as a concise inventory of packages.

```markdown
# Knowledge Package Registry

## Purpose
This registry lists reusable Layer 4 technical knowledge packages derived from generated manufacturing SME inputs.

## Source Inputs

| Input | Present | Notes |
|---|---:|---|
| sme-registry.md | <yes/no> | <notes> |
| smes/*.md | <count> | <notes> |
| shop-reference.md | <yes/no> | <notes> |
| user-uploaded documents | <yes/no> | <notes> |

## Packages

| Package | Type | Scope | Derived From SME(s) | Input Mapping Confidence | Technical Source Confidence | Source Tier Coverage | Source Basis | Limitations |
|---|---|---|---|---|---|---|---|---|
| `<package-name>` | <domain-general/process-family/process-subtype/equipment-family/machine-model/material-family/inspection-or-test-method/controls-software-settings> | <short scope> | <SME names> | <high/medium/low> | <high/medium/low/placeholder/not gathered> | <tiers or generated-input only> | <generated SME shell + sme-registry.md + shop-reference.md + public-source placeholders/user-doc based/mixed> | <limits> |

## Deferred Opportunities

| Candidate Package | Reason Deferred | Needed Source Or Input |
|---|---|---|
| `<candidate-package>` | <why not created now> | <needed support> |
```

Do not list package names that were not derived from inputs. Use deferred opportunities for plausible but unsupported packages.

Use `Input Mapping Confidence` for SME/package fit. Use `Technical Source Confidence` for the substantiation of technical content. If public sources were not actually gathered, set `Technical Source Confidence` to `placeholder`, `not gathered`, or `low`; do not use medium/high for placeholder-only technical support.

Example row behavior:

```markdown
| `example-process-package` | process-family | Process behavior named in generated SME shell | Example Process SME | high | placeholder | Generated SME shell; sme-registry.md; shop-reference.md; public-source placeholder | generated SME shell + sme-registry.md + shop-reference.md + public-source placeholders | No OEM/manual/setup-sheet support; not shop-approved instruction. |
```
