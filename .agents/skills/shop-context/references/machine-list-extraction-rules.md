# Machine List Extraction Rules

Use these rules when extracting manufacturing context from machine lists, asset lists, equipment tables, line cards, cell descriptions, or user-provided machine notes.

## Key Rule

Machine lists describe equipment context. They do not define the process sequence by themselves.

Use routers/work orders to establish operation sequence.
Use machine lists and attached operation instructions to support machine-to-operation and equipment-to-step mapping.
If a machine list conflicts with router flow, preserve both and flag the mismatch for review.

## Extracted Fields

Extract the following when present:

- Machine name
- Machine type
- Work center
- Associated operation
- Process capability
- Manual notes
- Asset number, serial number, line, cell, or location
- Fixtures, benches, stations, tooling, or other equipment names
- Explicitly confirmed records/logs only when stated by the source

## Machine Name

- Preserve the machine name exactly as shown.
- Keep model names, nicknames, and asset identifiers if provided.
- If the machine name is ambiguous, keep the raw source text and flag for review.

## Machine Type

Identify the machine type from explicit type fields, model names, or clear descriptions. Examples include stencil printer, pick-and-place, AOI, vapor phase reflow, selective solder, CNC mill, press, tester, inspection bench, or manual station.

If type is not stated or clearly probable, mark it unknown.

## Work Center

- Extract the work center exactly as shown.
- Do not invent a work center from machine location unless the source makes that relationship clear.
- If a machine appears in a work center not found in routers, keep it and flag the mismatch.

## Associated Operation

- Use explicit associated operation fields when present.
- Do not assign a machine to an operation unless the source supports it or the mapping is clearly probable.
- If multiple machines could perform the same operation, list all candidates and flag for review.
- If a machine is listed without a matching operation, keep it in the machine dictionary and flag it as unmapped.

## Process Capability

Capture stated capabilities such as:

- Stencil print
- Placement
- AOI
- Reflow
- Soldering
- Wash
- Conformal coat
- Cure
- Electrical test
- Functional test
- Inspection
- Packaging

Do not infer detailed capability limits such as tolerance, capacity, recipe, or program unless provided.

## Confirmed Records / Logs

Do not create generic evidence-source lists from machine type alone.

Only extract records/logs/forms/results when the machine list, asset export, operation instruction, or user note explicitly states that the shop creates, retains, exports, reviews, or uses them.

Place confirmed records/logs in the relevant Operation Step Summary in the final reference. If the record/log is machine-specific but not tied to an operation, keep a concise note in the Machine / Equipment Dictionary.

## Handling Incomplete Machine Lists

Incomplete machine lists are acceptable V1 inputs. Keep unmapped machines visible, mark missing fields as unknown, and create targeted open questions for high-value gaps.
