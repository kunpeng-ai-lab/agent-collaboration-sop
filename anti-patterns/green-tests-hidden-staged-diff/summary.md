# Anti-Pattern: Green Tests, Hidden Staged Diff

Redaction Status: reviewer-approved

## Summary

An Executor reports that tests pass and no product code changed. The Reviewer
checks only the default test command and might approve. However, staged changes
contain product code modifications that are outside the approved scope.

## Why This Is Dangerous

- Tests can pass while unapproved product changes exist.
- `git diff` alone does not show staged changes.
- Evidence ledger can look complete while omitting the real risk.
- Scope drift can be committed accidentally.

## Redaction Approval

Redaction reviewed by: <REVIEWER>
Redaction review date: 2026-05-06
Redaction result: approved
Redaction evidence path: this sanitized anti-pattern file
Remaining disclosure risk: low; no private paths, repos, screenshots, or raw
conversation logs included

