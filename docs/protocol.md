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

## Phase 1: Execution

Executor Agent:

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

## Phase 2: Review

Reviewer Agent:

- reviews code
- reviews architecture
- reviews engineering structure
- reviews product and project goal alignment
- runs tests or targeted verification
- checks evidence and redaction
- checks release/upstream risk
- writes findings

Reviewer Agent must not:

- treat green tests as enough
- ignore project goal drift
- skip evidence requirements
- approve vague handoffs

## Phase 3: Consensus Report

If review passes and next phase is proposed:

1. Reviewer writes a consensus report.
2. Owner reads and confirms.
3. Only after approval may Executor begin next phase.

## Phase 4: Evidence Ledger

For important work, create or update evidence ledger:

- screenshots
- PR links
- issue links
- commits
- CI status
- local verification
- reviewer approval
- Owner approval

