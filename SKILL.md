---
name: agent-collaboration-sop
description: Use when setting up or running two-agent collaboration in a shared project, especially an Executor agent paired with a Reviewer agent. Enforces communication routing, Owner approval gates, reviewer quality checks beyond code review, evidence ledgers, screenshots, project-goal alignment, technical design review, ACS sync rules, and ACS invocation phrases for Codex, Claude Code, OpenClaw, Hermes, or other agents.
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

## Mandatory ACS Sync

Before project work, read `docs/acs-sync-rules.md`.

Sync ACS when:

- it is 06:00 local time and scheduled jobs are available
- this is the first project task of the day
- Owner or Reviewer explicitly says to sync/update/use latest ACS

Required commands:

```powershell
cd <ACS 本地路径>
git pull origin main
git rev-parse --short HEAD
```

Report the ACS local path, current version, and whether `git pull origin main`
was executed. Do not claim sync without a version.

When latest ACS is explicitly requested, the ACS version changed, this is the
first project task of the day, or new ACS redlines may affect the task, run
`docs/acs-adoption-check.md`. ACS sync without adoption is incomplete.

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

## Message Format

All Owner-forwarded messages that should be copied to another agent must be
wrapped in a fenced code block.

If the client cannot reliably preserve fenced code blocks, use the fallback ACS
message envelope in `docs/message-envelope-rules.md`:

```text
<<<ACS_MESSAGE_BEGIN>>>
Message To Reviewer:
你好 <Reviewer>，我是 <Executor>。
Message ID: <YYYYMMDDHHmm-E01>
Responds To Message ID: <YYYYMMDDHHmm-R01>

<message body>

请按照 ACS 项目（<ACS 本地路径>）规范进行（测试/审核）。
<<<ACS_MESSAGE_END>>>
```

The begin marker must be the first line and the end marker must be the last
line. No text may appear outside the envelope.

For long handoffs, design packages, closure notes, or evidence summaries, do not
put the full content in chat. Use `docs/file-first-handoff-rules.md`: write the
full handoff to a project file, then send only the Message ID, file path, short
summary, and review request.

Every formal ACS message must include a Message ID according to
`docs/message-id-rules.md`, for example `Message ID: 202605061145-E01`.
Receivers must check whether the Message ID was already processed before acting.

Every Executor acknowledgement, blocked note, handoff, or review request must be
wrapped as one fenced code block. Inside that code block, include a clear
`Message To Reviewer` section and start with:

```text
你好 <Reviewer>，我是 <Executor>。
```

For example:

````text
```text
Message To Reviewer:
你好 Codex，我是 CC。

ACS 本地路径：D:\workspace\agent-collaboration-sop
ACS 当前版本：<git rev-parse --short HEAD>
已执行：git pull origin main

请按照 ACS 项目（D:\workspace\agent-collaboration-sop）规范进行（测试/审核）。
```
````

A screen-only confirmation or general note is not a closed loop.

## Workflow

1. Sync ACS according to `docs/acs-sync-rules.md`.
2. Initialize the project using `docs/initialization-questionnaire.md`.
3. Copy `templates/project-sop.md` into the target project's
   `docs/PROJECT_SOP.md`.
4. Record project short name, Owner title, Executor short name, Reviewer short
   name, ACS local path, scope, non-scope, exit criteria, and redline rules.
5. Executor prepares a development package for non-trivial work.
6. Executor implements only within approved scope and writes handoff using
   `templates/executor-handoff.md`.
7. Reviewer reviews using `templates/reviewer-report.md`,
   `docs/reviewer-quality-bar.md`, `docs/reviewer-testing-playbook.md`,
   `docs/reviewer-evidence-gates.md`,
   `docs/reviewer-product-validation.md`, and
   `docs/technical-design-rules.md`.
8. Reviewer sends Owner a consensus report using
   `templates/owner-consensus-report.md`.
9. At phase closure, add a sanitized case study or anti-pattern summary when the
   phase produced a reusable collaboration lesson.
10. Executor starts the next phase only after Owner approval.

## Reviewer Must Check

- ACS sync evidence
- ACS adoption evidence when required: files read, delta summary, behavior
  update, and memory/project-rule update confirmation
- Given / When / Then behavior scenarios for non-trivial work
- project goal alignment
- approved design and plan alignment
- architecture and module boundaries
- decoupling and dependency direction
- test coverage, including failure paths
- evidence ledger and screenshots
- four evidence gates: command, evidence, product, and architecture
- page-level or workflow-level validation for product-facing work
- security, redaction, credentials, local path leakage
- operational, release, upstream, and customer-visible risk
- whether important code and methods include useful human-debuggable comments

## Redline

Green tests are evidence, not approval.

For UI, prototype, report, public content, customer-visible, or workflow tasks,
page-level/product-level validation is mandatory. Tests alone are not enough.

Reviewer chat messages should include the review summary and detailed report
path. Detailed review, product validation, and evidence analysis belong in the
target project files.

ACS case studies and anti-patterns must be sanitized according to
`docs/case-study-redaction.md` before they are committed.

Reviewer redaction approval is mandatory for every case study or anti-pattern.
Unreviewed redaction blocks commit, publication, sharing, and reuse.

No ledger entry means the claim is not accepted as verified.

No ACS sync evidence means the handoff is incomplete.

No Message ID means the formal ACS message is incomplete.

Duplicate Message IDs must be treated as possible duplicate forwarding. Do not
repeat side-effectful work until clarified.

When ACS Adoption Check is required, a version number alone is not enough. The
agent must report files read, delta summary, behavior update, and
memory/project-rule update confirmation.

No behavior scenarios for non-trivial work means the development package is
incomplete.

No ACS invocation means the receiver must ask for correction before substantive
work starts.

Executor confirmations must include a clear `Message To Reviewer` section that
starts with `你好 <Reviewer>，我是 <Executor>。`

The whole `Message To Reviewer` must be inside a fenced code block. Screen-only
confirmation or general note is not a closed loop.

If a fenced code block is repeatedly stripped, truncated, or partially rendered
by the chat client, the whole `Message To Reviewer` must use the ACS fallback
envelope from `docs/message-envelope-rules.md`. Missing envelope boundaries or
extra text outside the envelope is not a closed loop.

If the message is too long for reliable chat copying, the Executor must switch
to file-first handoff. The Reviewer reviews the file, not the shortened chat
body.
