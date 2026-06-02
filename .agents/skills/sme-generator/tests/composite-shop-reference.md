# Composite Shop Reference

Expected behavior:

- Generate `Shop Flow SME`.
- Generate `Inspection SME`.
- Generate Machine / Capability SMEs from named freezer, ply cutter, layup table, vacuum pump/cart, autoclave, oven, router, drill bench, NDI equipment, visual inspection bench, surface prep station, bond fixture rack, paint booth, environmental monitor, and repair equipment.
- Do not generate broad Composite Layup, Vacuum Bagging, Cure, Paint, Kitting, Repair, or Maintenance SMEs by default unless represented as named machine/station/capability or user-requested.
- Conditional repair equipment should be Conditional, not Required.
- Generic stations without clear identity should be Needs Review.
- No CCA/electronics defaults should appear.
