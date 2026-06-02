# Operation-To-SME Mapping Rules

This reference is retained for compatibility. Operations no longer create separate SMEs by default.

Use operations to support:

- `Shop Flow SME`
- `Inspection SME`
- Machine / Capability SME status and context

## Procedure

For each operation:

1. Preserve operation number, operation name, work center, product/route scope, and route status.
2. Identify named machines, stations, cells, benches, equipment, or capabilities tied to the operation.
3. Attach those links to the relevant Machine / Capability SME.
4. Use operation route status to classify the SME:
   - standard operation -> Required
   - conditional/rework/repair/MRB/alternate/special/route-dependent operation -> Conditional
   - no operation support -> Optional / Capability Available or Needs Review
5. Send inspection, test, check, verify, final acceptance, and quality-gate information to `Inspection SME`.

## Do Not Generate By Default

Do not generate separate SMEs from operations such as:

- Kit Material
- Receive Material
- MRB Review
- Rework
- Pack
- Manual Assembly
- Material Traceability
- Testing

unless the source names a machine/station/cell/equipment asset/major capability or the user explicitly requests that SME.

## Management-Prep Boundary

When a manager asks which SMEs are relevant and explicitly does not want RCCA, keep the answer in management-prep mode: relevant SMEs, source links, records to bring, and meeting questions.

Do not declare root cause, recommend corrective action, say an issue was created at a step, or convert the answer into ProblemPath/RCCA routing unless the user asks for RCCA.
