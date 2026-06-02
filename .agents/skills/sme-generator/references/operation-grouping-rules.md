# Operation Grouping Rules

This reference is retained for compatibility. Operation grouping no longer creates task/process SMEs by default.

Group operations only to:

- summarize route flow in `Shop Flow SME`
- connect related operations to the same named machine/capability SME
- avoid duplicate machine/capability shells
- create open questions for ambiguous operation groups

## Examples

- Multiple operations using `Haas VF-2SS` should point to one `Haas VF-2SS SME`.
- Multiple inspection/check/verify operations should be coordinated by one `Inspection SME`, plus named inspection machine SMEs where applicable.
- `Op 020 Process` can support multiple named machine SMEs if the source says it uses multiple machines.

## Generic Operations

Generic operation names such as `Process`, `Inspect`, `Test`, `Verify`, `Check`, or `Assembly` should not create specific SMEs by themselves.

Resolve them only through source-provided machine/capability mappings and shop-specific terminology.
