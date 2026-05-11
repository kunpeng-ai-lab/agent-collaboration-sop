# Project SOP

## Project Identity

Project Name:
Project Short Name:
Repository:
Open Source Status:

ACS Repository:
ACS Local Path:

## Owner

Owner Title:
Owner Decision Items:

- new phase start
- scope change
- public release
- deployment
- upstream PR
- customer-visible report
- credential use
- commercial boundary

## Agents

Executor Agent:
Executor Short Name:

Reviewer Agent:
Reviewer Short Name:

Communication Mode:

- [ ] Single-responsibility: Executor implements, Reviewer reviews/tests/routes Owner decisions.
- [ ] Cross-review: each agent owns a different project and reviews the other project.

Approved Communication Route:

```text
Executor -> Reviewer -> Owner
Owner -> Reviewer -> Executor
```
Routing Exceptions:

## Current Phase

Phase Name:
Approved Scope:
Explicit Non-Scope:
Exit Criteria:
Required Verification:

## Redline Rules

1. Executor cannot self-approve.
2. Reviewer must review code, architecture, engineering structure, project goal alignment, tests, safety, evidence, and release risk.
3. Next phase cannot begin before Reviewer consensus report and Owner approval.
4. Scope changes require written discussion and Owner approval.
5. Public release, deployment, upstream PR, customer report, or credential usage requires Owner approval.
6. All important claims require evidence.
7. Important code and module methods must include human-debuggable comments.
8. Any test, verification, review, deployment, upstream PR, or customer-visible output must have a traceable ledger entry.
9. Visual, public, remote, CI, deploy, PR, forum, blog, or customer-visible evidence must include screenshots when practical.
10. Every non-trivial development unit must have plan, design notes, test cases, constraints, minimal-change strategy, documentation impact, and evidence plan.
11. Executor must keep changes minimal and scoped. Unrelated refactors require separate approval.
12. Reviewer must verify the evidence chain before asking Owner for approval.
13. Reviewer must challenge test coverage. Happy-path-only tests are not enough for risky work.
14. Reviewer must flag design, plan, architecture, or project-goal drift even when code runs and tests pass.
15. Architecture-affecting work must include technical research and design notes before coding.
16. Modules must be reasonably decoupled. Reviewer must reject avoidable tight coupling.
17. Design must state module boundaries, dependency direction, data flow, and failure behavior.
18. Executor does not communicate directly with Owner for normal execution; Executor messages to Owner go through Reviewer.
19. Owner does not bypass Reviewer to assign Executor work; Owner instructions are routed through Reviewer.
20. Reviewer is the direct Owner communication channel for approvals, decisions, and phase reports.
21. Reviewer -> Executor development/design tasks must include: "请遵循 ACS 项目（<ACS 本地路径>）规范进行（<设计/编码>）。"
22. Executor -> Reviewer review requests must include: "请按照 ACS 项目（<ACS 本地路径>）规范进行（<测试/审核>）。"
23. If ACS invocation is missing, the receiver must ask for correction before substantive work starts.
24. Executor acknowledgements, blocked notes, and handoffs must include a clear "Message To Reviewer" section. A screen-only confirmation is not a closed loop.
25. Agents must sync ACS at 06:00 when scheduled automation is available, or before the first project task of the day when automation is unavailable.
26. If Owner or Reviewer explicitly asks to sync/update/use latest ACS, the agent must sync immediately.
27. Handoffs and review requests must report ACS local path, ACS current version, and whether `git pull origin main` was executed.
28. Non-trivial work must include Given / When / Then behavior scenarios before implementation.
29. Reviewer must verify tests/evidence against the behavior scenarios.
30. Before proposing or starting a next phase, Reviewer and Executor must check the approved phase sequence, unfinished current-phase work, open findings, closeout gaps, and Owner decision items.
31. Agents must not discard, skip, rename, or reframe an approved plan because of a later chat message unless Owner explicitly approves the roadmap change.
32. If the latest instruction conflicts with the established plan, Reviewer must state the conflict and ask Owner for an explicit decision before instructing Executor.

## Development Package Requirements

Before non-trivial implementation, Executor must prepare:

- plan
- design notes
- Given / When / Then behavior scenarios
- technical/architecture research
- module boundaries
- dependency direction
- data flow
- failure behavior
- test cases
- constraints
- explicit non-scope
- minimal-change strategy
- documentation impact
- evidence plan
- rollback/recovery notes when relevant

Reviewer must approve the package before implementation when work is:

- architecture-affecting
- cross-module
- high-risk
- public/upstream/customer-visible
- security or credential related

## Handoff Rules

Executor must submit:

- development package reference
- changed files
- summary
- ACS sync evidence
- tests run
- verification evidence and screenshots
- risks
- explicit review request
- Message To Reviewer

Reviewer must submit:

- pass / needs changes
- findings
- verification
- test coverage assessment
- design/plan drift assessment
- technical design and decoupling assessment
- ledger links and screenshot/evidence references
- risks
- Owner decision items

## Evidence Locations

Evidence directory:

```text
evidence/
```

Ledger file:

```text
docs/EVIDENCE_LEDGER.md
```

Decision log:

```text
docs/DECISION_LOG.md
```
