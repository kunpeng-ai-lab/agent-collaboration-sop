# ACS Case Study Summary

Case ID: phase0-baseline-stabilization
Case Type: standard-case
Source Project: <PROJECT>
Source Phase: Phase 0 baseline stabilization
Date: 2026-05-06
Prepared By: <REVIEWER>
Reviewed By: <REVIEWER>
Redaction Status: reviewer-approved

## Redaction Checklist

- [x] Owner, Executor, and Reviewer identities generalized.
- [x] Private project names and repo URLs removed.
- [x] Local paths replaced with `<LOCAL_PATH>`.
- [x] Credentials, tokens, cookies, webhook URLs, and secrets removed.
- [x] Customer/commercial details generalized.
- [x] Screenshots omitted.
- [x] The reusable lesson is still understandable.

## Mandatory Reviewer Redaction Approval

No case study or anti-pattern may be committed, published, shared, or used as a
reference artifact before Reviewer redaction approval.

Redaction reviewed by:

- <REVIEWER>

Redaction review date:

- 2026-05-06

Redaction result:

- approved

Redaction evidence path:

- this sanitized case file and `docs/case-study-redaction.md`

Remaining disclosure risk:

- low; project identity, paths, repository details, screenshots, and raw
  conversation logs are omitted or generalized

## Phase Goal

Stabilize a newly transferred project baseline so future agents can trust the
default test command and evidence ledger before feature work starts.

## Approved Scope And Non-Scope

Scope:

- sync project SOP with ACS roles
- verify default tests
- confirm no unapproved product or prototype code changes
- record evidence and review results

Non-scope:

- no product feature work
- no prototype redesign
- no architecture cleanup without Owner approval
- no deployment or public release

## Conversation Timeline

| Step | Actor | Summary | Evidence |
| --- | --- | --- | --- |
| 1 | <OWNER> | Asked the team to take over a project and establish a trustworthy baseline. | Owner instruction summarized |
| 2 | <EXECUTOR> | Reported that tests were green and claimed zero product/prototype code changes. | Handoff summary |
| 3 | <REVIEWER> | Ran tests and inspected staged and unstaged diffs. Found that green tests did not prove scope compliance. | Command and git diff evidence |
| 4 | <EXECUTOR> | Identified a dirty local stash as the cause of the mismatch and restored the baseline. | Revised handoff |
| 5 | <REVIEWER> | Re-ran tests, checked staged/unstaged diffs, verified docs/evidence consistency, and approved closure. | Reviewer report |

## What Went Well

- Reviewer did not accept green tests as sufficient approval.
- Reviewer checked both staged and unstaged changes.
- Executor corrected the root cause instead of weakening tests.
- The team separated local dirty state from the actual project baseline.
- Evidence was updated after each correction.

## What Went Wrong Or Almost Went Wrong

- Initial handoff claimed zero code changes while staged changes existed.
- Evidence ledger initially contradicted git state.
- A stale local worktree could have been mistaken for the official baseline.
- Architecture debt could have been recorded incorrectly.

## Reviewer Lessons

- Always check `git diff --cached` in addition to `git diff`.
- Always compare evidence ledger claims with actual repository state.
- Tests passing does not prove scope compliance.
- When a project is newly transferred, dirty local state must be separated from
  official baseline state.
- Closure requires command, evidence, product/scope, and architecture gates.

## Executor Lessons

- Do not rely on one diff command when claiming zero code changes.
- Include staged and unstaged diff evidence in baseline work.
- If local state causes failures, diagnose the environment before changing tests.
- Keep handoff claims aligned with evidence files.

## Evidence Pattern

What evidence was decisive?

- commands:
  - `npm test`
  - `git status --short`
  - `git diff --stat`
  - `git diff --cached --stat`
  - `git diff -- <product-path>`
  - `git diff --cached -- <product-path>`
- screenshots:
  - not used; no UI change was approved
- diffs:
  - staged and unstaged diffs
- ledger:
  - baseline evidence ledger and reviewer report
- browser/page checks:
  - not required for closure because no product/prototype code changes remained

## ACS Rule Impact

This case clarified:

- Green tests are evidence, not approval.
- Staged diffs must be checked for scope-sensitive work.
- Evidence ledger claims must match repository state.
- Phase closure should produce reusable case-study or anti-pattern material when
  the collaboration lesson is transferable.

## Future Team Checklist

- [ ] Run default tests.
- [ ] Check staged and unstaged diffs.
- [ ] Check target product paths explicitly.
- [ ] Verify evidence ledger statements against actual commands.
- [ ] Do not convert local dirty state into project architecture debt.
- [ ] Record Reviewer report path in the handoff.

