# ACS Adoption Check

ACS sync is not complete until the agent adopts the new rules.

`git pull` proves the files arrived on the machine. It does not prove the agent
read, understood, or updated its working rules.

## When Required

Run an ACS Adoption Check after every ACS sync when:

- Owner or Reviewer explicitly requests latest ACS
- ACS version changed after `git pull`
- the task is the first project task of the day
- a new redline, template, review gate, or case-study rule was added
- Reviewer doubts that Executor is following the latest ACS behavior

## Required Adoption Evidence

The agent must report:

1. ACS local path
2. ACS current version
3. whether `git pull origin main` was executed
4. ACS files read after sync
5. delta summary: what changed or what rules matter now
6. behavior update: how the agent will change execution/review behavior
7. memory/project-rule update confirmation
8. limitations, if the agent cannot persist long-term memory

## Minimum Files To Read

At minimum, read:

- `SKILL.md`
- `docs/acs-sync-rules.md`
- `docs/reviewer-evidence-gates.md`
- `docs/reviewer-product-validation.md`
- `docs/case-study-redaction.md`
- `templates/reviewer-report.md`
- `templates/executor-handoff.md`

If the task is design-heavy, also read:

- `docs/technical-design-rules.md`
- `docs/bdd-principles.md`

If the task involves case studies or anti-patterns, also read:

- `templates/case-study-summary.md`
- `case-studies/README.md`
- `anti-patterns/README.md`

## Delta Summary Requirement

The agent must summarize the rules in its own words. Copying the document titles
is not enough.

Example:

```text
Delta summary:
- UI and prototype tasks require page-level validation, not only tests.
- Review must pass command, evidence, product, and architecture gates.
- Case studies and anti-patterns require Reviewer redaction approval before use.
- Chat messages should contain summaries and report paths; details belong in
  project files.
```

## Behavior Update Requirement

The agent must say how its behavior will change.

Example:

```text
Behavior update:
- In every UI review, I will open or inspect the page/workflow and record the
  validation report path.
- In every review, I will check staged and unstaged diffs.
- I will not approve a case study unless redaction approval is recorded.
```

## Memory And Project Rule Update

The agent must state one of:

```text
Memory/project rules updated: yes
```

or:

```text
Memory/project rules updated: no
Reason:
Project-local fallback:
```

If long-term memory cannot be updated, the agent must record the rules in the
current project handoff or project SOP and follow them for the session.

## Required Message Template

```text
ACS Adoption Check:
- ACS local path:
- ACS current version:
- Executed git pull origin main: yes / no
- Files read:
  - 
- Delta summary:
  - 
- Behavior update:
  - 
- Memory/project rules updated: yes / no
- Limitations:
  - 
```

## Reviewer Responsibility

Reviewer must reject ACS sync claims that include only a version number when an
Adoption Check is required.

ACS sync without adoption is incomplete.

