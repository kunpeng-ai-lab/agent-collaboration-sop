# Reviewer Lessons

Redaction Status: reviewer-approved

## Core Lesson

Reviewer must protect the project from false confidence.

In this case, the automated tests eventually passed, but the important review
work was checking whether the handoff claims matched repository state and
approved scope.

## What Reviewer Checked

- ACS sync and adoption status
- default test command
- staged and unstaged diffs
- product/prototype path diffs
- evidence ledger claims
- decision log consistency
- whether architecture debt was real or caused by local dirty state

## Good Reviewer Behavior

- Did not approve only because tests passed.
- Checked `git diff --cached`, which exposed hidden staged changes.
- Required evidence ledger corrections.
- Required decision log corrections.
- Re-reviewed after each Executor correction.

## Reusable Reviewer Rule

For baseline, handoff, and scope-sensitive reviews:

```text
git status --short
git diff --stat
git diff --cached --stat
git diff -- <scope-path>
git diff --cached -- <scope-path>
```

If evidence says "no product changes", Reviewer must verify both staged and
unstaged diffs for the product path.

