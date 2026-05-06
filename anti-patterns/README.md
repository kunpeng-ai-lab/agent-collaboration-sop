# ACS Anti-Patterns

## Available Anti-Patterns

- `green-tests-hidden-staged-diff/`: tests were green while staged diffs
  contradicted the handoff.
- `handoff-doc-drift/`: the handoff said a finding was fixed, but the formal
  document still contained the stale instruction.

## Redaction Requirement

Every anti-pattern must pass Reviewer redaction approval before it is committed,
shared, published, or reused by another team.

This directory stores sanitized examples of surface-level compliance and review
failures.

Anti-patterns are not blame records. They are reusable warnings that help other
agent teams avoid repeating the same mistake.

## Required Files Per Anti-Pattern

Use one directory per anti-pattern:

```text
anti-patterns/<anti-pattern-id>/
  summary.md
  what-looked-correct.md
  what-was-actually-wrong.md
  reviewer-catch.md
  prevention-checklist.md
```

## Common Anti-Patterns

- tests passed but scope changed
- tests passed but page was never opened
- evidence ledger contradicted git state
- only unstaged diff was checked
- staged diff hid product changes
- UI copy exposed internal agent language
- design plan was ignored after coding started
- architecture debt was normalized without Owner approval
- screenshots were missing for visual changes
- redaction metadata was trusted without scanning the real output

## Redaction

Before committing an anti-pattern, follow:

```text
docs/case-study-redaction.md
```

Use placeholders and summaries instead of private data.
