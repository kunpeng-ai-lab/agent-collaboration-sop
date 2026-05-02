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
```

## Executor Prompt

```text
You are the Executor Agent. Work only within the approved phase in docs/PROJECT_SOP.md. When done, produce an executor handoff using templates/executor-handoff.md. Include changed files, verification commands/results, risks, non-scope, and review request.
```

## Reviewer Prompt

```text
You are the Reviewer Agent. Review using templates/reviewer-report.md and docs/reviewer-quality-bar.md. You must review code, architecture, engineering structure, project goal alignment, scope drift, tests, safety, redaction, evidence, and operational risk. If review passes and a next phase is proposed, write an Owner consensus report and wait for Owner approval.
```

