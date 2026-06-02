# Public Package Cleanup Validation

## Purpose

Validate that the ShopFloor AI public package is clean, installable, and does not publish live root-level generated shop state.

## Checklist

| Check | Result | Notes |
|---|---:|---|
| Root package has no live generated `shop-reference.md` | pass | Moved to `examples/synthetic-injection-molding-shop/outputs/` |
| Root package has no live generated `sme-registry.md` | pass | Moved to example outputs |
| Root package has no live generated `sme-coverage.md` | pass | Moved to example outputs |
| Root package has no live generated `smes/` | pass | Moved to example outputs |
| Root package has no live generated `sme-knowledge-map.md` | pass | Moved to example outputs |
| Root package has no live generated `knowledge-package-registry.md` | pass | Moved to example outputs |
| Root package has no live generated `knowledge-packages/` | pass | Moved to example outputs |
| Generated synthetic outputs are under `examples/` | pass | `examples/synthetic-injection-molding-shop/outputs/` |
| Synthetic example is clearly labeled synthetic | pass | `examples/synthetic-injection-molding-shop/README.md` |
| `.shop-ai` contains templates only | pass | `state.template.md`, `onboarding-log.template.md` |
| `source-repos/` is not staged | pass | Excluded by `.gitignore` |
| All five skills are present | pass | ShopContext, SME Generator, SME Manager, SME Knowledge Builder, Step Automation |
| `AGENTS.md` is present | pass | Root agent guidance added |
| README explains install and MVP user flow | pass | README rewritten for public package |
| LICENSE is MIT | pass | `LICENSE` added |
| `.gitignore` protects generated local outputs | pass | Root generated outputs and local state ignored |
| No obvious private/sensitive data is staged | pass | Staged generated shop data is limited to the clearly labeled synthetic example under `examples/`; `source-repos/` and root local generated outputs are not staged |

## Notes

The included example data is synthetic and retained only under `examples/`. The public package root is intended to start clean so users can onboard their own shop by providing messy inputs and running `step-automation`.
