# Boundaries And Overclaiming Rules

Use conservative language. Knowledge packages strengthen SME reasoning; they do not create shop authority.

## Never Claim From Public Or Generated Sources Alone

Do not claim that a public source, SME shell, registry, or generated shop context proves:

- Actual shop settings
- Approved recipes
- Customer acceptance criteria
- Actual root cause
- Final corrective action
- Product disposition
- Compliance with drawings, specs, or contracts
- Maintenance history
- Operator action
- Actual machine state during a build

Do not use high Input Mapping Confidence as a substitute for technical evidence. A package may clearly belong to an SME while its Technical Source Confidence remains placeholder, not gathered, or low.

If public sources are listed only as placeholders, they may justify the intended package scaffold but do not substantiate technical claims as cited evidence.

## Machine-Specific Caution

Include machine-specific notes only when:

- The input names the machine or model.
- A reliable source covers that machine or model.
- The claim is clearly bounded to what the source supports.

If the input names a machine but sources are weak, create an equipment-family package or write a machine-specific limitation instead of inventing model detail.

## Exact-Machine Versus Machine-Family Separation

Keep these claim types separate:

- Exact-machine/model claim: requires an OEM/manual/datasheet/uploaded source for that exact model or a very close documented model family.
- Machine-family claim: can use credible equipment-family sources but must not be worded as a specific model capability.
- Shop-specific claim: requires generated SME shell/shop reference/user-uploaded shop document/actual record support.
- Actual-use claim: requires actual shop evidence or user confirmation.

If a source supports only the equipment family, write "in this equipment family..." rather than "this specific machine...".

If a generated SME shell says a machine is used in the shop, public sources may explain how that type of machine generally works, but they cannot approve settings, recipes, procedures, or job-specific decisions.

## Troubleshooting Logic Boundary

It is acceptable to explain how an experienced SME thinks through symptoms. Keep this as reasoning logic:

- Compare symptoms to process variables.
- Identify plausible mechanisms.
- Consider interactions between material, equipment, tooling, software, method, and environment.
- State uncertainty.

Do not turn this into a mandatory evidence request checklist unless the user explicitly asks for one outside this skill.

## Uploaded Document Boundary

For v0.1, mention uploaded-document support as a future upgrade path. If the user provides documents during the task, use them as source inputs and label them clearly, but do not build full Layer 5 behavior unless requested.

## Language Patterns

Prefer:

- "This package supports general understanding of..."
- "The source supports equipment-family principles, not shop-approved settings."
- "The SME shell names this capability, but no machine-model source was found."
- "This may help reason about symptoms, but cannot prove root cause."

Avoid:

- "The shop should..."
- "The approved setting is..."
- "The root cause is..."
- "This proves..."
- "Accept/reject the part based on..."

## Depth Without Overreach

Deeper packages should explain mechanisms and variables, not issue instructions. Prefer:

- "Moisture can contribute to molding instability because..."
- "A surface plate supports stable manual measurement, but the inspection plan controls the method."
- "Press setup, material condition, tooling, and cooling can interact; records are needed to separate them."

Avoid:

- "Use this setting..."
- "Change this parameter..."
- "This defect was caused by..."
- "This part fails..."
