# ShopContext

ShopContext turns messy manufacturing shop documents into a clean `shop-reference.md` file that AI can use to understand how a specific shop works.

## What It Does

ShopContext reads files like:

- routers
- work orders
- PRTs / travelers
- operation work instructions
- machine / asset lists
- shop notes
- acronym lists
- user corrections

Then it creates a reusable `shop-reference.md` that explains:

- operation flow
- operation meanings
- hidden steps inside vague operations
- work centers
- machines / equipment
- quality gates
- shop-specific language

## Why It Matters

Manufacturing data is usually messy.

Common problems:

- different names for the same process
- same word meaning different things
- vague operation names
- instructions hidden in PDFs or Word docs
- machine lists not mapped to operations
- legacy exports
- missing work centers
- duplicate asset names

ShopContext gives AI the shop dictionary it needs before answering manufacturing questions.

## Simple Example

Router says:

```text
Op 0200 - Process Secondary Side
```

Attached instruction says the operation includes:

```text
solder paste -> pick-and-place -> vapor phase -> wash -> bake -> inspection
```

ShopContext summarizes Op 0200 as a multi-step SMT process instead of treating it as one vague operation.

## Output

The main output is:

```text
shop-reference.md
```

Final structure:

```md
# Shop Reference

## 1. Shop Type / Process Context
## 2. Standard Operation Flow
## 3. Operation Dictionary
## 4. Operation Step Summaries
## 5. Work Center Dictionary
## 6. Machine / Equipment Dictionary
## 7. Quality Gates
## 8. Shop-Specific Language
```

## How To Use

Example prompt:

```text
Use the ShopContext skill on these files:

- router_export.md
- op_0200_work_instruction.md
- machine_list.md
- shop_notes.md

Generate the ShopContext Review and draft final shop-reference.md.
```

Workflow:

1. Upload available shop files.
2. Run ShopContext.
3. Review questions or low-confidence items.
4. Correct anything needed.
5. Save the final `shop-reference.md`.

## What It Is Not

ShopContext is not:

- an RCCA solver
- a root-cause engine
- a corrective action generator
- a defect trend analyzer
- an SPC tool
- a live MES/QMS/ERP integration

It creates shop context. It does not solve defects.

## Validation

ShopContext has passed simulated validation for:

| Test | Stress Case | Result |
|---|---|---|
| CCA hidden steps | Vague op with attached instruction | Passed |
| Machining PRT | One PRT with many ops | Passed |
| Harness five PNs | Same flow, different names/granularity | Passed |
| Bad input quality | Missing, conflicting, duplicate data | Passed |

## Design Rules

- Preserve exact operation numbers, names, work centers, and machine names.
- Do not assume router operations are atomic.
- Use attached instructions to find hidden internal steps.
- Normalize meaning without deleting original shop terms.
- Do not invent missing instructions.
- Do not fake machine-to-operation mappings.
- Keep the final reference lean.
- Preserve uncertainty when the source data is uncertain.

## Current Limits

- Real PDF/DOCX parsing still needs real-use validation.
- Image-heavy instructions may need OCR or manual export.
- Very large file sets have not been performance-tested.
- User correction loop still needs end-to-end validation.
