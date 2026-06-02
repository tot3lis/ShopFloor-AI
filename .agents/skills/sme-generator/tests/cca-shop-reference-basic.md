# CCA Shop Reference Basic

Expected behavior under the simplified SME Generator architecture:

- Generate `Shop Flow SME`.
- Generate `Inspection SME`.
- Generate named Machine / Capability SMEs from CCA machines and stations in the source, such as stencil printer, placement machine, AOI, reflow equipment, inspection station, and named tester.
- Do not generate CCA process/task SMEs by default.
- Do not generate Kitting, MRB, Material Traceability, Maintenance / Equipment, or Testing SMEs by default unless represented as named equipment/station/capability or user-requested.
- Treat CCA/electronics as one supported shop type, not as the default SME universe.
- Keep all auto-generated shells at Level 3 unless actual manuals, specs, work instructions, or evidence records are provided.
