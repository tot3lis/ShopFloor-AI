# ShopContext Validation Summary

This file summarizes the completed simulated validation scenarios for the standalone ShopContext manufacturing AI prep skill.

ShopContext creates a lean, AI-readable `shop-reference.md` from messy manufacturing shop documents. The final reference is expected to use the 8-section structure defined by the skill:

1. Shop Type / Process Context
2. Standard Operation Flow
3. Operation Dictionary
4. Operation Step Summaries
5. Work Center Dictionary
6. Machine / Equipment Dictionary
7. Quality Gates
8. Shop-Specific Language

## Validation Summary Matrix

| Scenario | Purpose | Files | Expected Behavior | Status |
|---|---|---|---|---|
| CCA hidden-step test | Validate that a vague router operation can be decomposed using an attached work instruction. | `sample-router-with-hidden-steps.md`<br>`sample-attached-work-instruction-op0200.md`<br>`sample-machine-list-realistic.md`<br>`sample-shop-notes.md`<br>`expected-shop-reference-behavior.md` | Op `0200 Process Secondary Side` is not treated as atomic. The attached instruction reveals paste, PNP, vapor phase, wash, bake, and inspection. Machine/manual/quality context is folded into Operation Step Summaries. Final output uses the lean 8-section structure. | Passed simulated validation. |
| Machining multi-op PRT test | Validate one PRT/instruction document containing multiple operation sections. | `sample-router-machining-shared-wo.md`<br>`sample-prt-machining-multi-op-instruction.md`<br>`sample-machine-list-machining-unmapped.md`<br>`sample-shop-notes-machining.md`<br>`expected-shop-reference-behavior-machining.md` | One PRT is split into operation-specific summaries. Shared WO/traveler is preserved without merging operations. Machine list without op mappings supports context but does not create fake certainty. `M-12` asset mismatch remains uncertain. | Passed simulated validation. |
| Harness five-PN terminology/granularity test | Validate cross-part shop-language normalization across five part numbers. | `sample-router-harness-five-pns.md`<br>`sample-prt-harn-1001.md`<br>`sample-prt-harn-1002.md`<br>`sample-prt-harn-1003.md`<br>`sample-prt-harn-1004.md`<br>`sample-prt-harn-1005.md`<br>`sample-machine-list-harness-unmapped.md`<br>`sample-shop-notes-harness.md`<br>`expected-shop-reference-behavior-harness-five-pns.md` | Recognizes one harness shop/process family across five PNs. Groups same-meaning operations with different names. Preserves PN-specific granularity differences. Handles combined operations and split operations correctly. Does not invent machine-to-op mappings. | Passed simulated validation. |
| Bad input quality test | Validate graceful uncertainty handling with missing, conflicting, duplicated, and incomplete shop data. | `sample-router-bad-input-quality.md`<br>`sample-prt-cca-ctrl-9001-smt.md`<br>`sample-prt-cca-pwr-9010-unclear-headers.md`<br>`sample-machine-list-bad-quality.md`<br>`sample-shop-notes-bad-quality.md`<br>`expected-shop-reference-behavior-bad-input-quality.md` | Missing `WI-CCA-9002-SMT.docx` is not fabricated. Poor PRT headers are interpreted with uncertainty. Router-vs-PRT wash contradiction is preserved. Shop notes clarify wash/bake without hiding source conflict. Duplicate/alias machine rows are preserved cautiously. Retired equipment is not treated as active. Conflicting work centers are preserved. Final output remains lean. | Passed simulated validation. |

## Current Validation Status

ShopContext has passed simulated validation for:

- hidden steps inside attached operation instructions
- multi-operation PRT documents
- multi-part-number terminology and granularity normalization
- bad input quality / uncertainty handling

## Known Limitations / Next Validation Targets

- Real uploaded PDF/DOCX parsing still needs validation.
- OCR/image-heavy instructions are not yet validated.
- Very large file sets have not been performance-tested.
- The user correction loop should be tested end-to-end.
- The final generated `shop-reference.md` should be tested as context for downstream manufacturing Q&A.

## Scope Guardrails

The completed validations preserve the current ShopContext scope:

- no root cause analysis
- no corrective action generation
- no defect trend analysis
- no SPC analysis
- no dynamic data integration
- no larger-system routing behavior
