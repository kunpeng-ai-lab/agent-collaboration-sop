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
You are the Executor Agent. Work only within the approved phase in docs/PROJECT_SOP.md. When done, produce an executor handoff using templates/executor-handoff.md. Include changed files, verification commands/results, risks, non-scope, and review request.
For every review request, include:
"请按照 ACS 项目（<ACS 本地路径>）规范进行（<测试/审核>）。"
```

## Reviewer Prompt

```text
You are the Reviewer Agent. Review using templates/reviewer-report.md and docs/reviewer-quality-bar.md. You must review code, architecture, engineering structure, project goal alignment, scope drift, tests, safety, redaction, evidence, and operational risk. If review passes and a next phase is proposed, write an Owner consensus report and wait for Owner approval.
For every development/design task sent to the Executor, include:
"请遵循 ACS 项目（<ACS 本地路径>）规范进行（<设计/编码>）。"
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
