# ACS Redacted Collaboration Cases

Status: public-safe draft
Redaction status: sanitized

## Case 1: Baseline Stabilization And Hidden Diff Review

### Situation

A team transferred a project into an ACS workflow. The first goal was not to
add features. The goal was to establish a trustworthy baseline: default tests
should run, scope should be clear, and the evidence ledger should match the
repository state.

### Executor Action

The Executor reported that tests passed and that no product/prototype code had
changed. A handoff summarized the verification and asked Reviewer to close the
baseline phase.

### Reviewer Finding

The Reviewer did not stop at the test result. They checked staged and unstaged
diffs separately and found that the repository state contradicted the handoff.
The issue was not that tests failed; the issue was that passing tests did not
prove the phase stayed inside approved scope.

### Owner Decision

The Owner accepted closure only after the dirty state was explained, evidence
was updated, and the Reviewer re-ran the relevant checks. The team treated the
case as a reusable ACS lesson: check staged diffs, unstaged diffs, product paths,
and evidence ledgers before approving a baseline.

### Reusable Lesson

Green tests are not approval. Baseline closure requires command evidence,
repository-state evidence, scope evidence, and a Reviewer report.

## Case 2: Implementation Package Review Before Coding

### Situation

A team prepared an implementation package for a product phase. The Executor
needed to specify pages, modules, tests, evidence, and stop conditions before
starting code changes.

### Executor Action

The Executor submitted a design package with BDD scenarios, file plans,
screenshots, test commands, and evidence paths.

### Reviewer Findings

The Reviewer blocked the package across multiple rounds:

- some new tests would not run under the default test command;
- target pages were assumed to be empty even though existing content was
  present;
- product-language changes were hidden inside an encoding workaround;
- a handoff claimed a stale command was removed while the formal design document
  still contained it.

### Owner Decision

The Owner decided the product UI language must remain the approved language and
that encoding should be solved as an engineering problem, not by silently
changing product direction. Coding was allowed only after the implementation
package, tests, evidence plan, and stop conditions became coherent.

### Reusable Lesson

Reviewer must check files, not just handoff summaries. Design-package approval
is a gate before coding, especially when product UI, encoding, tests, and
evidence plans interact.

## Case 3: Contract Design Before Integration Coding

### Situation

One platform needed another agent system to perform diagnosis, planning,
validation, reporting, and correction work. The Owner required staging/mock
mode with dry-run only before any real integration.

### Executor Action

The Executor prepared a design-only contract package: request envelope,
response envelope, status mapping, write-back intents, tenant boundaries,
report boundaries, BDD scenarios, and test/evidence plan.

### Reviewer Finding

The Reviewer found that the package described version compatibility but did not
include a concrete `contractVersion` field in the request envelope. This meant
future implementation could not reliably fail closed on unknown contract
versions.

### Owner Decision

The Owner kept the phase design-only. The Executor corrected the contract by
adding version fields, fail-closed error behavior, audit evidence, BDD
scenarios, and test plan coverage. Reviewer approved the design after verifying
typecheck, tests, build, and document consistency.

### Reusable Lesson

Integration design must make safety checks executable. If a design says "reject
unknown versions," the contract must contain a field that implementation and
tests can validate.

## Case 4: Human QA Feedback Into Prototype Repair

### Situation

Human testers reviewed a prototype and found usability gaps: buttons did not
give visible feedback, navigation names were hard to map to expected workflows,
and evidence-oriented pages were not easy to discover.

### Executor Action

The Executor implemented mock/prototype-only fixes: visible button feedback,
evidence navigation, workbench interactions, and menu alias help. The work was
kept out of real backend, database, and deployment boundaries.

### Reviewer Finding

The Reviewer first found that a menu-alias explanation existed only as hidden
metadata, so a human tester could not see it. After repair, the Reviewer checked
that the visible UI no longer had a long top-navigation text that crowded the
layout.

### Owner Decision

The Owner allowed deployment of the prototype for further human QA only after
Reviewer verification, evidence screenshots, tests, commit/push, and remote
deployment checks.

### Reusable Lesson

Product validation requires human-visible evidence. Metadata that helps tests
but not users does not close a usability finding.

