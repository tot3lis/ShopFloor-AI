# SME Naming Rules

The default generated SME names are:

- `Shop Flow SME`
- `Inspection SME`
- `[Machine / Capability Name] SME`

## Machine / Capability Names

Use exact source names when available:

- `DEK Horizon SME`
- `MY200 SME`
- `Koh Young Zenith SME`
- `Haas VF-2SS SME`
- `Paint Booth PB-3 SME`

Normalize only enough to create a readable file name and registry row. Preserve the exact source name inside the profile shell.

## Capability Names

Use a capability SME only when the source gives a capability but not a uniquely named machine or station:

- `CNC Mill SME`
- `Manual Soldering Bench SME`
- `Harness Test Station SME`
- `Bonding Station SME`

## Do Not Generate By Default

Do not generate these names unless user-requested or represented as named equipment/station/capability:

- Kitting SME
- MRB SME
- Rework SME
- Material Traceability SME
- Maintenance / Equipment SME
- Testing SME
- Manual Assembly SME

## File Names

Use lowercase kebab-case:

- `shop-flow-sme.md`
- `inspection-sme.md`
- `dek-horizon-sme.md`
- `koh-young-zenith-sme.md`
