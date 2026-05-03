# Install And Use

## Use In A Project

Copy templates into your target project:

```text
templates/project-sop.md -> docs/PROJECT_SOP.md
templates/executor-handoff.md -> docs/<phase>-executor-handoff.md
templates/reviewer-report.md -> docs/<phase>-reviewer-report.md
templates/owner-consensus-report.md -> docs/<phase>-owner-consensus-report.md
templates/evidence-ledger.md -> docs/<work-item>-evidence-ledger.md
```

Record the ACS local path in the target project's `docs/PROJECT_SOP.md`.

Example:

```text
ACS Local Path: E:\workspace\agent-collaboration-sop
```

## Sync ACS Before Work

Before project work, apply `docs/acs-sync-rules.md`.

If automation is available, schedule a daily sync at 06:00 local time.

If automation is not available, sync ACS before the first project task of the
day.

If Owner or Reviewer explicitly says "同步 ACS", "更新 ACS", or "按最新 ACS 执行",
sync ACS immediately.

```powershell
cd <ACS 本地路径>
git pull origin main
git rev-parse --short HEAD
```

Every handoff or review request must report:

- ACS local path
- ACS current version
- whether `git pull origin main` was executed
- failure reason if sync failed

## First Prompt To Any Agent Pair

```text
We are using Agent Collaboration SOP.

Before implementation, ask the Owner the initialization questionnaire:
- project formal name
- project short name
- Owner title
- Executor Agent name and short name
- Reviewer Agent name and short name
- current phase
- allowed scope
- explicit non-scope
- required verification

Write the answers into docs/PROJECT_SOP.md. Do not start development until this is done.
Also record the ACS repository URL, local ACS path, and communication route:
Executor -> Reviewer -> Owner and Owner -> Reviewer -> Executor.
```

## Executor Prompt

```text
You are the Executor Agent. Work only within the approved phase in docs/PROJECT_SOP.md.
Before your first task of the day, or whenever Owner/Reviewer asks, sync ACS:
cd <ACS 本地路径>
git pull origin main
git rev-parse --short HEAD

When done, produce an executor handoff using templates/executor-handoff.md.
Include changed files, ACS sync evidence, verification commands/results, risks,
non-scope, and review request.

For every review request, include:
请按照 ACS 项目（<ACS 本地路径>）规范进行（<测试/审核>）。
```

## Reviewer Prompt

```text
You are the Reviewer Agent. Review using templates/reviewer-report.md and docs/reviewer-quality-bar.md.
You must review code, architecture, engineering structure, project goal alignment,
scope drift, tests, safety, redaction, evidence, ACS sync evidence, and operational risk.
If review passes and a next phase is proposed, write an Owner consensus report and wait for Owner approval.

For every development/design task sent to the Executor, include:
请遵循 ACS 项目（<ACS 本地路径>）规范进行（<设计/编码>）。
```

If an agent has already saved older ACS wording in memory, project rules, or a
local prompt, explicitly ask it to overwrite the old wording with the templates
above.

## Communication Routing

Use `docs/communication-routing.md` as the default rule:

```text
Executor -> Reviewer -> Owner
Owner -> Reviewer -> Executor
```

The Executor does not directly ask the Owner for decisions. The Owner does not
bypass the Reviewer to assign Executor work. The Reviewer consolidates Owner
intent, ACS constraints, and review expectations before forwarding instructions
to the Executor.
