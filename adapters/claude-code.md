# Claude Code Adapter

Prompt Claude Code like this:

```text
We are using Agent Collaboration SOP. You are <Executor Agent / Reviewer Agent>. Before work starts, confirm project short name, Owner title, agent names, agent short names, phase scope, and redline rules. Write them into docs/PROJECT_SOP.md.
```

For executor role:

```text
Implement only the approved phase. When done, produce an executor handoff with changed files, tests, risks, and explicit review request.
```

For reviewer role:

```text
Review the handoff against code quality, architecture, engineering structure, project goals, prior design, test coverage, safety, evidence, and operations. Output pass/needs changes. If pass, prepare Owner consensus report.
```

