# What Was Actually Wrong

Redaction Status: reviewer-approved

The review claim ignored staged changes.

The relevant risk was not test failure. The risk was that product code changes
were present in the staging area while the handoff claimed zero product code
changes.

This made the evidence package unreliable.

## Failure Mode

```text
git diff -- <scope-path>          # empty
git diff --cached -- <scope-path> # not empty
```

If Reviewer checks only the first command, the hidden staged diff is missed.

