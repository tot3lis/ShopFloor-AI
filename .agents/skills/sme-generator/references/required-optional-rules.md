# Required / Optional Rules

Use `sme-status-classification-rules.md` as the primary status source.

Each SME must be classified as exactly one of:

- Required
- Conditional
- Optional / Capability Available
- User-requested
- Not Detected
- Needs Review

## Required

Use Required for:

- `Shop Flow SME`
- `Inspection SME`
- Machine / Capability SMEs tied to standard route operations

## Conditional

Use Conditional for machine/capability SMEs tied only to conditional, alternate, special, route-dependent, rework, repair, MRB, or optional operations.

## Optional / Capability Available

Use Optional / Capability Available for named machines/capabilities listed in the source but not tied to standard operation flow.

## Needs Review

Use Needs Review when the machine/capability exists but its support, route status, or operation mapping is ambiguous.

## Default Generation Boundaries

- Do not generate SMEs from every operation/task by default.
- Do not generate separate Kitting SME by default.
- Do not generate separate MRB SME by default.
- Do not generate separate Rework SME by default unless a named rework station/capability exists or the user explicitly requests it.
- Do not generate Manual Assembly SME by default unless a named assembly cell/station/capability exists.
- Do not generate Material Traceability SME by default.
- Do not generate Maintenance / Equipment SME by default. Maintenance belongs inside each machine/capability shell as documents to request later.
- Do not generate Testing SME by default unless there is a named test machine, test station, or test capability. `Inspection SME` can coordinate test handoff questions from the reference.

## Examples

| Source Evidence | Expected Assignment |
|---|---|
| Standard route operation uses `DEK Horizon` | `DEK Horizon SME` = Required |
| Standard route operation uses `Hioki Tester` | `Hioki Tester SME` = Required |
| `Inspection` quality gate exists | `Inspection SME` = Required |
| CMM named for inspection | `Inspection SME` = Required and `Zeiss Contura G2 SME` = Required or Conditional based on route status |
| Repair equipment used only for conditional repair | named repair equipment SME = Conditional |
| Active equipment listed but not used in provided route | named equipment SME = Optional / Capability Available |
| `Station 12` listed with no operation mapping | `Station 12 SME` = Needs Review |
| Kit Material with no named kitting station | no separate Kitting SME by default |
| MRB Review with no named MRB station/capability | no separate MRB SME by default |
