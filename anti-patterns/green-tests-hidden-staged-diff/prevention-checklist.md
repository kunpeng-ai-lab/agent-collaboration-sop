# Prevention Checklist

Redaction Status: reviewer-approved

Before approving "tests pass and no product changes":

- [ ] Run the default test command.
- [ ] Check `git status --short`.
- [ ] Check `git diff --stat`.
- [ ] Check `git diff --cached --stat`.
- [ ] Check `git diff -- <scope-path>`.
- [ ] Check `git diff --cached -- <scope-path>`.
- [ ] Compare evidence ledger statements with command output.
- [ ] Require Owner approval for any product or architecture change outside
      approved scope.

