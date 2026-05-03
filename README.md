# Agent Collaboration SOP

Maintained by **Kunpeng AI Exploration Bureau / kunpeng-ai-lab / 鲲鹏 AI 探索局**.

Official site: [kunpeng-ai.com](https://kunpeng-ai.com)
GitHub: [kunpeng-ai-lab](https://github.com/kunpeng-ai-lab)

Agent Collaboration SOP, abbreviated as **ACS**, is a vendor-neutral workflow for
two-agent engineering collaboration. It works with Codex, Claude Code,
OpenClaw, Hermes, and other coding agents that can read project files, edit code,
run tests, and produce handoffs.

## What ACS Solves

ACS is designed for teams that use one agent as the Executor and another as the
Reviewer.

It prevents common failures:

- the Executor self-approves its own work
- the Reviewer only runs tests and misses architecture or goal drift
- Owner decisions are lost in chat history
- scope changes slip into implementation without approval
- tests pass but the work violates the approved design
- public, upstream, or customer-visible claims lack screenshots or ledger proof

## Default Collaboration Model

ACS defaults to single-responsibility collaboration.

| Role | Responsibility |
| --- | --- |
| Owner | Final decision maker for goals, scope, phase entry, release, upstream PRs, and business boundaries |
| Executor Agent | Designs within approved scope, implements, self-tests, documents, and writes handoff |
| Reviewer Agent | Reviews design, code, tests, architecture, goal alignment, evidence, safety, and reports consensus to Owner |

Cross-review mode is an advanced variant and should be used only when the Owner
explicitly assigns it.

## Communication Routing

Long-term route:

```text
Executor -> Reviewer -> Owner
Owner -> Reviewer -> Executor
```

- Executor does not directly communicate with Owner during normal execution.
- Executor messages to Owner are routed through Reviewer.
- Owner instructions to Executor are routed through Reviewer.
- Reviewer consolidates Owner intent, ACS constraints, and review expectations.

See [docs/communication-routing.md](docs/communication-routing.md).

## Mandatory ACS Invocation

Every development/design task from Reviewer to Executor must include:

```text
Please follow the ACS project standards for design/coding.
ACS project path: E:\workspace\agent-collaboration-sop
```

Every review request from Executor to Reviewer must include:

```text
Please test and review according to ACS (E:\workspace\agent-collaboration-sop)
project standards.
```

If your local ACS clone is somewhere else, replace the path and record it in the
target project's `docs/PROJECT_SOP.md`.

## Quick Start

1. Clone ACS:

```powershell
git clone git@github.com:kunpeng-ai-lab/agent-collaboration-sop.git E:\workspace\agent-collaboration-sop
```

2. Copy templates into the target project:

```text
templates/project-sop.md -> docs/PROJECT_SOP.md
templates/executor-handoff.md -> docs/<phase>-executor-handoff.md
templates/reviewer-report.md -> docs/<phase>-reviewer-report.md
templates/owner-consensus-report.md -> docs/<phase>-owner-consensus-report.md
templates/evidence-ledger.md -> docs/<work-item>-evidence-ledger.md
```

3. Ask the Owner the initialization questions in
   [docs/initialization-questionnaire.md](docs/initialization-questionnaire.md).

4. Record project name, project short name, Owner title, Executor short name,
   Reviewer short name, ACS local path, scope, non-scope, exit criteria, and
   redline rules in `docs/PROJECT_SOP.md`.

5. Start work only after the approved phase is clear.

## Reviewer Quality Bar

The Reviewer must check more than whether the code runs.

Reviewer must review:

- project goal alignment
- approved design and plan alignment
- architecture and module boundaries
- decoupling and dependency direction
- test coverage, including failure paths
- security, credentials, redaction, and leakage risk
- evidence ledger and screenshots
- release, deployment, upstream, and customer-visible risk
- whether important code and module methods are human-debuggable

See:

- [docs/reviewer-quality-bar.md](docs/reviewer-quality-bar.md)
- [docs/reviewer-testing-playbook.md](docs/reviewer-testing-playbook.md)
- [docs/technical-design-rules.md](docs/technical-design-rules.md)
- [docs/engineering-governance.md](docs/engineering-governance.md)

## Project Structure

```text
agent-collaboration-sop/
  README.md
  CONTRIBUTING.md
  docs/
    communication-routing.md
    initialization-questionnaire.md
    protocol.md
    naming-rules.md
    reviewer-quality-bar.md
    reviewer-testing-playbook.md
    technical-design-rules.md
    engineering-governance.md
  templates/
    project-sop.md
    executor-handoff.md
    reviewer-report.md
    owner-consensus-report.md
    evidence-ledger.md
  adapters/
    codex.md
    claude-code.md
    openclaw.md
    hermes.md
  examples/
    single-responsibility-example.md
```

## License

MIT.
