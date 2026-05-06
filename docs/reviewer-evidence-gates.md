# Reviewer Evidence Gates

ACS reviews must pass four evidence gates. Green tests are only one gate.

## Gate 1 - Command Gate

Reviewer verifies the executable checks relevant to the task.

Examples:

- test command
- typecheck
- build
- lint
- targeted regression test
- smoke test
- CLI command

Record:

- command
- working directory
- result
- failures, warnings, or skipped checks

## Gate 2 - Evidence Gate

Reviewer verifies that the evidence supports the claimed conclusion.

Check:

- evidence ledger exists
- command outputs are captured
- screenshots exist when needed
- staged and unstaged diffs are checked
- links, PRs, deploys, or CI states are recorded when relevant
- the evidence does not contradict the handoff

Required for git-based work:

```text
git status --short
git diff --stat
git diff --cached --stat
```

For scope-sensitive work, also check target paths:

```text
git diff -- <path>
git diff --cached -- <path>
```

## Gate 3 - Product Gate

Reviewer verifies that the result solves the actual user/product problem.

Use `docs/reviewer-product-validation.md` for product-facing work.

Check:

- user role
- workflow completion
- UX copy
- visible states
- empty/error states when relevant
- screenshot or equivalent visual evidence

## Gate 4 - Architecture Gate

Reviewer verifies that the implementation respects the approved design and
future direction.

Check:

- module boundaries
- dependency direction
- adapter/interface boundaries
- schema or contract consistency
- failure behavior
- decoupling
- scope and non-scope
- project short-term and long-term goals

## Summary In Chat, Detail In Files

Every review handoff should include a short gate summary in chat:

```text
Evidence gates:
- Command gate: pass
- Evidence gate: pass
- Product gate: pass / not applicable / needs changes
- Architecture gate: pass
Detailed report: reviews/<phase>/codex-review.md
```

The detailed gate report must be stored in the target project.

Recommended path:

```text
reviews/<phase>/codex-review.md
```

## Blocking Rules

Review must return `needs changes` when:

- command results are claimed but not reproducible
- evidence contradicts the handoff
- product-facing work has no page/workflow validation
- implementation drifts from approved architecture
- scope-sensitive paths changed without approval
- staged changes are not checked

