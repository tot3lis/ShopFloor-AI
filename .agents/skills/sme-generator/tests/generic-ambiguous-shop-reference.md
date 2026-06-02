# Generic Ambiguous Shop Reference

Expected behavior:

- Generate `Shop Flow SME`.
- Generate `Inspection SME`.
- Do not infer process/task SMEs from generic operation names such as `Process`, `Assembly`, `Inspect`, `Test`, `Verify`, or `Check`.
- Generate Machine / Capability SMEs only for named machines, stations, cells, benches, equipment, or major capabilities.
- Generic stations or machines with unclear support should be Needs Review.
- Machine-only capabilities with no standard operation support should be Optional / Capability Available or Needs Review.
