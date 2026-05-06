# Sanitized Conversation Excerpts

Redaction Status: reviewer-approved

This file summarizes the useful conversation pattern without exposing private
project names, local paths, screenshots, or repository URLs.

## Excerpt 1: Reviewer Blocks Test Coverage Theater

Executor summary:

> New tests will be added under a phase-specific subdirectory.

Reviewer response:

> The default test command only runs top-level test files. If new tests are not
> in the default gate, the baseline can look green while Phase 1 tests never run.

Reusable lesson:

- A test that is not in the default gate is evidence only if the handoff clearly
  runs it and the default command is not the agreed gate. Otherwise, reject.

## Excerpt 2: Reviewer Checks The Current File, Not The Plan Assumption

Executor summary:

> The target pages are placeholders to be completed.

Reviewer verification:

> Local inspection shows the target sections already contain substantial content.
> The plan must audit what exists, then preserve, repair, or replace intentionally.

Reusable lesson:

- Page work must start with a current-state audit. "Placeholder" is not a safe
  assumption.

## Excerpt 3: Owner Decides Product Language

Executor summary:

> Fix garbled text into readable ASCII English.

Reviewer escalation:

> ASCII is acceptable for docs, but product UI language is a product decision.
> Owner must decide whether the product UI stays Chinese.

Owner decision summary:

> Product UI stays Chinese. Solve UTF-8 correctly instead of switching language.

Reusable lesson:

- Encoding problems are engineering problems. Do not solve them by changing the
  product audience.

## Excerpt 4: Handoff Claim Does Not Match Formal Doc

Executor summary:

> Fragile inline command was replaced by a standalone script.

Reviewer verification:

> The formal implementation package still contains the old inline command.
> Handoff and document disagree, so coding cannot start.

Reusable lesson:

- Reviewer must inspect the formal artifact, not just the chat summary.
