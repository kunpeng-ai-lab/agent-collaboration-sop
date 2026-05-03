# Reviewer Testing Playbook

This playbook strengthens the testing role in Agent Collaboration SOP.

Reviewer testing is not a formality. The reviewer must actively try to prove
that the implementation satisfies the approved design and fails safely.

## 1. Test Strategy Review

Before accepting a handoff, reviewer must inspect the executor's test plan.

The plan must name:

- behavior under test
- happy paths
- failure paths
- boundary cases
- regression cases
- security/redaction cases
- integration or E2E cases when modules interact
- what is intentionally not tested and why

If the test plan is missing, vague, or only covers the happy path, review should
return `needs changes`.

## 2. Risk-Based Test Matrix

Reviewer should create or validate a small risk matrix:

| Risk | Required test type | Evidence |
| --- | --- | --- |
| Core behavior can regress | unit or integration test | test name + result |
| Bad input can break runtime | malformed input test | test name + result |
| Permission/gate can be bypassed | negative security test | test name + result |
| Sensitive data can leak | redaction/export test | test name + result |
| Module boundary can drift | contract/integration test | test name + result |
| User workflow can fail | E2E or smoke test | command + screenshot/log |

## 3. Reviewer Must Run Tests

Reviewer must run at least one verification command unless impossible.

Examples:

```text
npm test
npm run typecheck
npm run build
pnpm exec vitest run <target-test-file>
pytest <target-test-file>
go test ./...
```

Reviewer must record:

- command
- working directory
- exact result
- failures or warnings
- date/time when useful

## 4. Reviewer Must Add Targeted Tests When Needed

If existing tests miss an important risk, reviewer may request tests or add a
small targeted test in review mode when the project workflow allows it.

High-value reviewer test types:

- "should reject malformed input"
- "should block without approval"
- "should not mark evidence as redacted unless redaction ran"
- "should not advertise unsupported capability"
- "should not call external network in dry-run"
- "should preserve existing public API"
- "should fail closed when config is missing"

## 5. Design Drift Testing

Reviewer must test against the approved design, not just code behavior.

Ask:

- Does the implementation still follow the approved architecture?
- Does it use the agreed adapter/interface/schema?
- Does it skip an approved gate?
- Does it implement a future feature without approval?
- Does it make a claim that was not verified?

Design drift findings are valid even when every automated test passes.

## 6. Evidence Requirements

Testing evidence must be traceable.

Required:

- local command output in reviewer report
- ledger entry for important verification
- screenshot for UI, CI, GitHub, deploy, public post, or dashboard state
- links to logs/artifacts where applicable

Do not approve with "I tested it" unless the evidence is recorded.

## 7. Coverage Gap Language

Reviewer should be explicit:

```text
PASS, with non-blocking gap:
- No E2E test for real platform API because v1 scope is interface-only.

NEEDS CHANGES:
- Missing negative test for rejected approval gate.
- Current tests only cover success path.
```

## 8. Minimum Reviewer Checklist

Before pass:

- [ ] I checked the approved plan/design.
- [ ] I checked explicit non-scope.
- [ ] I inspected test coverage.
- [ ] I ran relevant verification.
- [ ] I checked failure paths.
- [ ] I checked security/redaction/export gates when relevant.
- [ ] I checked evidence ledger/screenshot requirements.
- [ ] I listed remaining coverage gaps.
- [ ] I identified Owner decision items.

