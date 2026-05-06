# Reviewer Catch

Redaction Status: reviewer-approved

Reviewer caught the issue by checking staged and unstaged diffs separately.

Required checks:

```text
git status --short
git diff --stat
git diff --cached --stat
git diff -- <scope-path>
git diff --cached -- <scope-path>
```

Reviewer then required the Executor to clarify whether the staged product diff
was inherited dirty state or an intended scope change.

Approval was withheld until the evidence and repository state matched.

