# SME Status Classification Rules

Each generated SME must be classified as exactly one of:

- Required
- Conditional
- Optional / Capability Available
- User-requested
- Needs Review
- Not Detected

## Required

Use Required when:

- the SME is `Shop Flow SME`
- the SME is `Inspection SME`
- a machine/capability is tied to a standard route operation

Example:

`DEK Horizon` mapped to standard `020 Process` -> `DEK Horizon SME = Required`.

## Conditional

Use Conditional when a machine/capability is tied only to:

- alternate operations
- special requirements
- route-dependent use
- rework
- repair
- MRB
- optional operations
- conditional operations

Example:

`Repair Hot Bonder` mapped only to conditional repair -> `Repair Hot Bonder SME = Conditional`.

## Optional / Capability Available

Use Optional / Capability Available when a named machine/capability appears in the source but is not tied to standard operation flow.

Example:

`Paint Booth` appears in an asset list but no paint operation appears in standard flow -> `Paint Booth SME = Optional / Capability Available`.

## Needs Review

Use Needs Review when a machine/capability exists but the reference does not clearly say what it supports.

Example:

`Station 12` listed with no operation mapping or description -> `Station 12 SME = Needs Review`.

## User-requested

Use User-requested when the user explicitly asks to add an SME that is not generated from the source.

User-requested SMEs must still use the router-ready profile shell and include routing triggers, contribution format, boundaries, and source-depth rules.

## Not Detected

Use Not Detected only in coverage notes for SME types or capabilities with no source support.

## De-Emphasized Defaults

Do not generate these as separate SMEs by default:

- Kitting SME
- MRB SME
- Rework SME
- Manual Assembly SME
- Material Traceability SME
- Maintenance / Equipment SME
- Testing SME

Create them only when represented as a named machine, station, cell, equipment asset, major capability, or when the user explicitly requests them.
