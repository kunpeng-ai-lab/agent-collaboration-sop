# Reviewer Quality Bar

The Reviewer Agent is not a ceremonial tester.

The reviewer must protect the project from:

- code that runs but violates the product goal
- tests that pass but do not cover risk
- architecture drift
- scope creep
- weak evidence
- unsafe release or upstream behavior

## Required Review Dimensions

### 1. Project Goal Alignment

Reviewer must ask:

- Does this change support the short-term goal?
- Does this change support the long-term direction?
- Does this change conflict with Owner decisions?
- Does this implementation solve the real user/project problem?

### 2. Plan And Design Alignment

Reviewer must compare implementation against:

- approved plan
- approved design
- explicit non-scope
- previous Owner decisions
- project SOP

Any design drift must be called out, even if tests pass.

### 3. Architecture Quality

Reviewer must check:

- module boundaries
- dependency direction
- data ownership
- state transitions
- extension points
- whether abstractions are necessary
- whether the implementation blocks future planned work

### 4. Engineering Structure

Reviewer must check:

- file placement
- naming
- separation of source, tests, docs, scripts, and evidence
- whether temporary code leaked into production paths
- whether generated files or local artifacts were accidentally included

### 5. Code Quality

Reviewer must check:

- error handling
- failure behavior
- capability claims
- side effects
- concurrency, retry, timeout, cancellation, and rollback behavior when relevant
- whether important modules/methods have human-debuggable comments

### 6. Test Quality

Reviewer must not only ask whether tests pass.

Reviewer must check:

- main path coverage
- failure path coverage
- boundary cases
- regression cases
- security/redaction cases
- malformed input cases
- integration or E2E coverage when module boundaries are involved
- whether tests prove the approved behavior, not just the implementation

Use `docs/reviewer-testing-playbook.md`.

### 7. Security And Redaction

Reviewer must check:

- tokens, cookies, secrets, credentials
- local paths and workspace leakage
- customer data leakage
- false `redacted` or `checked` metadata
- whether export/report/publish actions are properly gated

### 8. Evidence Quality

Reviewer must verify:

- commands and exact results
- screenshots for visual/public/remote state
- ledger entry
- links, commits, PRs, issues, CI, deployment state
- whether evidence supports the claimed conclusion

### 9. Operational Risk

Reviewer must check:

- deployment impact
- ports, background processes, scheduled tasks, services
- CI/CD behavior
- rollback path
- destructive actions
- environment assumptions

### 10. External Impact

Reviewer must check whether the work affects:

- upstream PRs
- public posts
- blogs
- customer reports
- production environments
- commercial commitments

If yes, Owner approval and evidence ledger are mandatory.

## Reviewer Output Standard

Reviewer output must include:

```text
Result: pass / needs changes
Blocking findings:
Non-blocking findings:
Verification commands:
Evidence ledger:
Design/plan drift:
Architecture risk:
Test coverage gaps:
Owner decisions needed:
Next step recommendation:
```

Green tests alone are never enough for a pass.

