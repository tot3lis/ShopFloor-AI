# Status Messages

## Purpose

Define the short user-facing setup status messages for `$shopfloor-ai`.

Use these messages during onboarding, setup, regeneration, or update runs so the user can see what the pipeline is doing without seeing internal routing details.

## When To Show Status Messages

Show status messages before and/or after major pipeline steps:

- detecting and using chat-attached or pasted shop files
- creating or finalizing `shop-reference.md`
- generating SME files
- generating knowledge packages
- entering ready state

Keep each status to one short sentence.

## Preferred Messages

Before ShopContext:

> Using ShopContext to generate the shop reference file.

After ShopContext succeeds:

> Shop reference file created.

Before SME Generator:

> Using SME Generator to generate shop SMEs.

After SME Generator succeeds:

> Shop SMEs generated.

Before SME Knowledge Builder:

> Using SME Knowledge Builder to generate knowledge packages.

After SME Knowledge Builder succeeds:

> Knowledge packages generated.

When ready:

> ShopFloor AI is ready. You can now ask shop questions in plain English.

## Blocking ShopContext Questions

If ShopContext finds mandatory blocking questions, stop and say:

> ShopContext needs a few confirmations before setup can continue.

Then ask only the mandatory questions.

Do not show a long mapping draft unless ShopContext explicitly requires it.

## No Inputs Available

If no chat-attached files, pasted data, optional `inputs/` files, or existing `shop-reference.md` are available, do not proceed to SME Generator.

Ask the user to drop in routers, work orders, machine lists, operation exports, or shop notes.

## When Not To Show Status Messages

Do not show setup status messages when:

- answering normal shop questions after `ready_for_questions` is enabled
- using SME Manager in normal question mode
- the user asks for a concise answer
- the user did not ask to run onboarding, setup, regeneration, validation, or update work

Do not show:

- internal routing details
- file lists
- debug output
- package names
- source-depth details

unless the user explicitly asks for explain/debug output.
