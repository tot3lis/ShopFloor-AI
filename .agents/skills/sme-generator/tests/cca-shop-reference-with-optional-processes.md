# CCA Shop Reference With Optional Processes

## Shop Overview

Example CCA shop reference with standard SMT operations plus equipment that is not tied to a standard router operation.

## Source Documents Reviewed

- Example router export
- Example equipment list

## Product Families

- Circuit card assemblies

## Standard Operation Flow

| Operation | Work Center | Operation Name | Machine / Context |
|---|---|---|---|
| Op 010 | MAT-KIT | Kit Material | Kitting bench |
| Op 020 | SMT-PRINT | Screen Print | DEK Horizon |
| Op 030 | SMT-PNP | Pick and Place | MY200 |
| Op 040 | SMT-AOI | AOI | Koh Young |
| Op 050 | SMT-VP | Vapor Phase | VAC 545 |
| Op 060 | QC-VIS | Final Inspect | Manual Inspection |
| Op 070 | TEST-ELEC | Electrical Test | Electrical test fixture |

## Operation Dictionary

- Op 010 Kit Material
- Op 020 Screen Print / DEK Horizon
- Op 030 Pick and Place / MY200
- Op 040 AOI / Koh Young
- Op 050 Vapor Phase / VAC 545
- Op 060 Final Inspect / Manual Inspection
- Op 070 Electrical Test

## Machine-To-Operation Map

- DEK Horizon -> Op 020 Screen Print
- MY200 -> Op 030 Pick and Place
- Koh Young -> Op 040 AOI
- VAC 545 -> Op 050 Vapor Phase
- Electrical test fixture -> Op 070 Electrical Test

## Equipment Listed With No Confirmed Standard Router Operation

- Conformal Coat Booth
- Bonding Dispenser

## Open Mapping Questions

- Is Conformal Coat Booth used for any standard routed operation?
- Is Bonding Dispenser used for a standard operation, special route, or engineering-only process?

## Expected Behavior

- Conformal Coat SME = Optional
- Bonding / Dispense SME = Optional
- Confidence = Low or Medium
- Open questions required
- No claim that these are standard operations
