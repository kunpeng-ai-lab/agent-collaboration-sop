# Collaboration Protocol

## Phase 0: Initialization

Before any work:

1. Ask the initialization questionnaire.
2. Confirm project name and short name.
3. Confirm Owner title.
4. Confirm Executor Agent name and short name.
5. Confirm Reviewer Agent name and short name.
6. Confirm current phase scope and non-scope.
7. Write everything into `docs/PROJECT_SOP.md`.
8. Confirm the local ACS path and write it into `docs/PROJECT_SOP.md`.
9. Confirm the communication route in `docs/communication-routing.md`.

Default communication route:

```text
Executor -> Reviewer -> Owner
Owner -> Reviewer -> Executor
```

The Executor does not directly ask the Owner for decisions. The Reviewer is the
single review and decision-routing channel.

Mandatory invocation:

- Reviewer -> Executor development/design tasks must include:
  "Please follow the ACS project standards for design/coding."
- Executor -> Reviewer review requests must include:
  "Please test and review according to ACS (<local ACS path>) project standards."

## Phase 1: Execution

Executor Agent:

- prepares a development package before non-trivial work
- records plan, design, test cases, constraints, minimal-change strategy, and docs impact
- researches relevant product, technical, framework, architecture, and operational context before designing
- defines module boundaries, dependency direction, data flow, and failure behavior for non-trivial changes
- works only within approved scope
- edits code/docs
- runs self-tests
- records evidence
- prepares handoff

Executor Agent must not:

- self-approve
- start next phase
- publish externally without approval
- hide scope changes inside implementation
- skip design/research for architecture-affecting work
- introduce tightly coupled modules without review
- skip required comments on important modules/methods
- claim verification without a traceable ledger entry

## Phase 2: Review

Reviewer Agent:

- reviews the development package when required
- reviews code
- reviews architecture
- reviews technical design, module decoupling, dependency direction, and stability assumptions
- reviews engineering structure
- reviews product and project goal alignment
- reviews whether important modules/methods are human-debuggable
- runs tests or targeted verification
- challenges the executor's test coverage and adds/request tests for gaps
- checks evidence and redaction
- checks screenshots and traceability ledger for important verification/review
- checks release/upstream risk
- writes findings

Reviewer Agent must not:

- treat green tests as enough
- accept tests that only cover the happy path for risky work
- ignore design drift because code runs
- accept tightly coupled design because tests pass
- accept implementation without required technical/architecture research
- ignore project goal drift
- skip evidence requirements
- accept untraceable test, verification, deploy, PR, or customer-visible claims
- approve vague handoffs
- accept a handoff that omits the mandatory ACS invocation
- allow Owner-to-Executor bypass unless the project SOP records an approved
  emergency exception

## Phase 3: Consensus Report

If review passes and next phase is proposed:

1. Reviewer writes a consensus report.
2. Owner reads and confirms.
3. Only after approval may Executor begin next phase.

## Phase 4: Evidence Ledger

For any testing, verification, review, deployment, upstream PR, or customer-visible work, create or update evidence ledger:

- screenshots
- PR links
- issue links
- commits
- CI status
- local verification
- reviewer approval
- Owner approval

Rule:

```text
No ledger entry -> not accepted as verified.
No screenshot for visual/public/remote state -> not accepted as traceable.
```

## Phase 5: Owner Evidence Chain

Before Owner approval is requested, Reviewer must provide:

- approved scope and non-scope
- completed work
- verification commands and exact results
- evidence ledger and screenshot links
- reviewer decision
- remaining risks
- exact Owner decision requested
