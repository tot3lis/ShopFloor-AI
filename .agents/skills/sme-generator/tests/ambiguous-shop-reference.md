# Ambiguous Shop Reference

## Shop Overview

Example shop reference with generic operation names and weak machine context.

## Source Documents Reviewed

- Example partial router
- Example machine list

## Product Families

- Circuit card assemblies

## Standard Operation Flow

| Operation | Work Center | Operation Name | Machine / Context |
|---|---|---|---|
| Op 020 | 100 | Process | Not specified |
| Op 030 | 200 | Inspect | Bench A or Bench B |
| Op 040 | 300 | Test | Generic Tester |

## Operation Dictionary

- Op 020 Process: unresolved processing step.
- Op 030 Inspect: inspection type not specified.
- Op 040 Test: test type not specified.

## Work Center Dictionary

- 100: unresolved
- 200: unresolved
- 300: unresolved

## Machine List

- Bonding Dispenser
- Coating Booth
- Bench A
- Bench B
- Generic Tester

## Machine-To-Operation Map

- Bench A -> Op 030 Inspect
- Bench B -> Op 030 Inspect
- Generic Tester -> Op 040 Test

## Open Mapping Questions

- What process occurs at Op 020 Process?
- Is Op 030 Inspect manual visual inspection, AOI review, or another inspection type?
- Is Op 040 Test electrical test, functional test, or another test type?
- Are Bonding Dispenser and Coating Booth production equipment or optional capabilities?

## Expected Behavior

- Do not force Op 020 into Bonding / Dispense SME or Conformal Coat SME.
- Do not force Op 030 into a single inspection SME without support.
- Do not force Op 040 into a confirmed test-equipment SME without a named test machine/station/capability or clearer support.
- Mark ambiguous assignments Needs review.
- Create targeted open questions.
