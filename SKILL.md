---
name: agent-collaboration-sop
description: Use when setting up or running two-agent collaboration in a shared project, especially an Executor agent paired with a Reviewer agent. Enforces communication routing, Owner approval gates, reviewer quality checks beyond code review, evidence ledgers, screenshots, project-goal alignment, technical design review, and ACS invocation phrases for Codex, Claude Code, OpenClaw, Hermes, or other agents.
---

# Agent Collaboration SOP

Use ACS when two agents collaborate on the same project or shared repository.

Default roles:

- Executor: plans within approved scope, implements, self-tests, documents, and
  writes handoff.
- Reviewer: reviews design, code, architecture, engineering structure, tests,
  evidence, project-goal alignment, safety, and reports consensus to Owner.
- Owner: makes final decisions on scope, phase entry, release, upstream PRs,
  customer-visible output, and business boundaries.

## Mandatory Communication Route

```text
Executor -> Reviewer -> Owner
Owner -> Reviewer -> Executor
```

The Executor does not directly ask the Owner for decisions. The Owner does not
bypass the Reviewer to give execution instructions. The Reviewer consolidates
Owner intent, scope, constraints, and ACS requirements before sending work to the
Executor.

## Mandatory ACS Invocation

Reviewer -> Executor development/design task:

```text
请遵循 ACS 项目（<ACS 本地路径>）规范进行（<设计/编码>）。
```

Executor -> Reviewer acknowledgement/review request:

```text
请按照 ACS 项目（<ACS 本地路径>）规范进行（<测试/审核>）。
```

Replace `<ACS 本地路径>` with the real local ACS clone path. Replace
`<设计/编码>` or `<测试/审核>` with the actual task type.

If an agent has already stored an older ACS wording in memory or local rules, it
must replace that wording with the templates above.

## Workflow

1. Initialize the project using `docs/initialization-questionnaire.md`.
2. Copy `templates/project-sop.md` into the target project's
   `docs/PROJECT_SOP.md`.
3. Record project short name, Owner title, Executor short name, Reviewer short
   name, ACS local path, scope, non-scope, exit criteria, and redline rules.
4. Executor prepares a development package for non-trivial work.
5. Executor implements only within approved scope and writes handoff using
   `templates/executor-handoff.md`.
6. Reviewer reviews using `templates/reviewer-report.md`,
   `docs/reviewer-quality-bar.md`, `docs/reviewer-testing-playbook.md`, and
   `docs/technical-design-rules.md`.
7. Reviewer sends Owner a consensus report using
   `templates/owner-consensus-report.md`.
8. Executor starts the next phase only after Owner approval.

## Reviewer Must Check

- project goal alignment
- approved design and plan alignment
- architecture and module boundaries
- decoupling and dependency direction
- test coverage, including failure paths
- evidence ledger and screenshots
- security, redaction, credentials, local path leakage
- operational, release, upstream, and customer-visible risk
- whether important code and methods include useful human-debuggable comments

## Redline

Green tests are evidence, not approval.

No ledger entry means the claim is not accepted as verified.

No ACS invocation means the receiver must ask for correction before substantive
work starts.

Executor confirmations must include a clear `Message To Reviewer` section. A
screen-only confirmation or general note is not a closed loop.
