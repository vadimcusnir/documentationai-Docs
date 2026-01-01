COD:: IDENTITY_ENGINE.ORDER.READ TTL=90z

## Invocation order for 02_IDENTITY_ENGINE

This file defines the minimal, strict read/invocation order for the Identity Engine layer. It is a contract for contributors and operators.

1. `architecture/00_MANIFEST/ORDER.READ`
2. `architecture/01_CONSTITUTION/CORE.VOICE`
3. `architecture/01_CONSTITUTION/RULE.TRUTH`
4. `architecture/01_CONSTITUTION/STYLE.NOEMOJI`
5. `architecture/02_MEMORY_OS/TTL_POLICY`
6. `architecture/02_IDENTITY_ENGINE/ORDER.READ` _(this file)_
7. Identity Engine layer specs and implementations

Niciun alt fișier nu este permis în această secvență minimă pentru Identity Engine.

## Rules

- Do not bypass the Constitution; always load `CORE.VOICE`, `RULE.TRUTH` and `STYLE.NOEMOJI` before any Identity Engine logic.
- Do not reference quarantine or enforcement subsystems directly from Identity Engine; route such intents via Systems OS.
- Do not extend or shorten TTL for Identity Engine state outside the constraints defined in `TTL_POLICY` (use `TTL=90z` for this contract).
- Do not read or write Memory OS ledgers (`DECISION.LEDGER`) from Identity Engine without an explicit, documented flow in Systems OS.
- Do not introduce additional mandatory files into this ordered chain without updating this contract.

## When data is missing

When the Identity Engine is invoked and required identity data, configuration, or upstream files are missing or inconsistent:

- Return the normalized error `ERR.NO_DATA`.
- Do not attempt silent recovery by fabricating identity attributes or default identities.
- Do not degrade into partial identity modes without an explicit higher-level policy defined outside this layer.
- Log or record the `ERR.NO_DATA` condition in the appropriate Memory OS mechanism, respecting TTL and scope policies from `TTL_POLICY`.