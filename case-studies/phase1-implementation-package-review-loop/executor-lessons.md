# Executor Lessons

Redaction Status: reviewer-approved

## 1. Build The Package From The Current Snapshot

Before writing an implementation package, inspect the current files. Do not rely
on stale memory or previous screenshots.

Minimum checks:

- current file line count
- target IDs and selectors
- existing script imports
- current test command
- current product page content

## 2. Make Tests Part Of The Default Gate

If the project uses `npm test`, new tests should run under `npm test` unless the
Owner and Reviewer approve a separate gate.

## 3. Do Not Hide Product Changes Inside Technical Fixes

If a change affects what users see, say so explicitly. Product language,
workflow, and page hierarchy are not "just implementation details."

## 4. Treat Handoff As A Contract

The handoff summary and formal document must match. If the handoff says a stale
command was removed, the document must not contain that stale command.

## 5. Use Scripted Checks For Repeatable Gates

Avoid fragile one-liners for important quality gates. Prefer scripts with
clear inputs, outputs, and exit codes.

## 6. Provide Evidence Paths Up Front

A strong handoff names:

- command output files
- screenshot directory
- product validation report
- line-count evidence
- scope-check evidence
- encoding-check evidence
