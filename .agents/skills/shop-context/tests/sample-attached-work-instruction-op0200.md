# Sample Attached Work Instruction - Op 0200

Synthetic copied work instruction for ShopContext validation. This file simulates content copied out of a PDF or Word work instruction. It is intentionally noisy and should not be treated as a polished procedure.

## Document Control Block

```text
Doc ID: WI-CCA-0200-SEC-SIDE
Title: CCA Secondary Side Processing
Revision: C
Related Router Operation: Op 0200 - Process Secondary Side
Applies To: CCA-PSU-CTRL-A2 Rev G and later unless otherwise noted
Owner: Manufacturing Engineering
Training: Operators must be current to SMT-STD-12 and ESD-001
```

## Safety / ESD / Setup Notes

- Wear heel straps and wrist strap at the secondary SMT line.
- Verify ESD bench monitor is green before handling assemblies.
- Do not stack bare CCAs.
- Use nitrile gloves when handling washed boards.
- Confirm solder paste is within floor-life window before use.
- If the DEK printer setup screen does not match this instruction, stop and call Manufacturing Engineering.
- Operator initials are required in the traveler after paste print, after reflow, and after bake unload.

## Materials And Equipment

```text
Stencil: STN-PSU-A2-SEC
Solder paste: SAC305 Type 4, no-clean
Printer: DEK Horizon, Asset SMT-PRN-014
Placement: MY200, Asset SMT-PNP-022
Reflow: VAC 545, Asset SMT-VP-003
Wash: Aqueous Washer AW-3, Asset WASH-003
Bake: Blue M Bake Oven, Asset OVEN-090
Inspection: 10x bench microscope or AOI review station if flagged
```

## Copied Instruction Text

1. Load `STN-PSU-A2-SEC` into the DEK Horizon. Check stencil orientation. Wipe underside before first print.
2. Print solder paste on the secondary side using the released program `PSU_A2_SEC_PASTE`.
3. Operator to verify paste coverage on U12, J4, and the fine-pitch regulator area. Do not repair paste bridges with a blade unless authorized by the lead.
4. Move panel to MY200 line. Load placement program `PSU_A2_SEC_PLACE`.
5. Place all secondary side SMT components. Verify feeder setup against the MY200 setup screen and traveler kit labels.
6. Send populated panel through VAC 545 vapor phase reflow using recipe `VP_SAC305_STD`.
7. Allow panel to cool before handling. Do not flex the panel when removing it from the carrier.
8. Wash assemblies in Aqueous Washer AW-3. Use standard CCA wash cycle `CCA_STD_07`.
9. Bake washed assemblies at 90°C for 45 minutes minimum in Blue M Bake Oven. Record oven load and unload time on the traveler.
10. After bake, perform post-process inspection. Look for solder balls, tombstoned components, paste smears, missing parts, and visible wash residue.
11. If defects are found, tag the traveler and move to MRB hold area. Do not continue to Op 0300 without lead approval.

## Footer Noise

```text
Printed copies are uncontrolled.
Page 1 of 3
See ENG-CCA-199 for stencil storage.
Do not use this instruction for CCA-PSU-CTRL-A1.
```

## Expected ShopContext Notes

- Treat this as the detailed instruction behind router operation `0200 Process Secondary Side`.
- Summarize the internal steps as solder paste application, pick-and-place, vapor phase reflow, wash, bake at `90°C`, and post-process inspection.
- Preserve important shop terms and equipment names such as `DEK Horizon`, `MY200`, `VAC 545`, `Aqueous Washer AW-3`, and `Blue M Bake Oven`.
- Include `traveler` signoffs and oven load/unload time only as confirmed records/logs because this instruction explicitly requires them.
- Do not copy this full instruction into final `shop-reference.md`.
