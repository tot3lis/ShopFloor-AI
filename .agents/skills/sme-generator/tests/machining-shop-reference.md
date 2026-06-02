# Machining Shop Reference

Expected behavior:

- Generate `Shop Flow SME`.
- Generate `Inspection SME`.
- Generate Machine / Capability SMEs from named equipment and capabilities such as saw, laser, waterjet, CNC mills/lathes, drill press, tapping station, press brake, washer, CMM, vision measurement, manual inspection bench, and outside-process work centers.
- Do not generate broad task SMEs such as Cutting, CNC Machining, Deburr, Wash, Packaging, or Kitting by default unless the source names a machine/station/capability for them.
- Classify machines tied to standard route operations as Required.
- Classify alternate, when-required, or not-always-used machines as Conditional.
- Classify active equipment with no route operation as Optional / Capability Available.
- Do not introduce CCA/electronics SMEs.
