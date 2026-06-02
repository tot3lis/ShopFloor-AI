# Cable Harness Shop Reference

Expected behavior:

- Generate `Shop Flow SME`.
- Generate `Inspection SME`.
- Generate Machine / Capability SMEs from named cutters, strippers, marking equipment, crimp tools, solder stations, overmold/protection cells, pull testers, electrical testers, form-board areas, label printers, and splicing equipment.
- Do not generate broad Wire Prep, Crimping, Testing, Kitting, Material Traceability, Rework, or Maintenance SMEs by default.
- Named test equipment such as Cirris should create a machine/capability SME; Inspection SME coordinates test handoff and acceptance-document questions.
- Traceability statements remain source context unless the user explicitly requests a separate traceability SME.
- Non-route active equipment should be Optional / Capability Available.
