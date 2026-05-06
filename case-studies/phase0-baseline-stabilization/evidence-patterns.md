# Evidence Patterns

Redaction Status: reviewer-approved

## Pattern 1 - Test Result Is Necessary But Not Sufficient

Record:

- command
- working directory category, not private path
- test count
- pass/fail count

Do not conclude approval from this alone.

## Pattern 2 - Staged And Unstaged Diff Pair

For every scope-sensitive claim, record both:

```text
git diff --stat
git diff --cached --stat
```

For product or source paths, record both:

```text
git diff -- <scope-path>
git diff --cached -- <scope-path>
```

## Pattern 3 - Evidence Ledger Consistency

The ledger must match real command output.

Reviewer should reject when:

- ledger says no product changes but product path diff exists
- ledger says tests changed but test diff is empty
- ledger records architecture debt that no longer exists
- ledger omits untracked or staged files

## Pattern 4 - Closure Re-Review

After Executor fixes evidence or scope issues, Reviewer should re-run the
commands rather than trusting the revised handoff.

