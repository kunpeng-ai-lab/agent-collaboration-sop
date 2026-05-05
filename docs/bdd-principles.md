# BDD Principles

BDD means Behavior-Driven Development.

In ACS projects, BDD is mandatory for non-trivial work because agents can easily
optimize for "code runs" while missing the real project behavior.

## Core Rule

For every non-trivial task, Executor must define key behavior scenarios before
implementation using:

```text
Given <context>
When <action>
Then <expected behavior>
```

Reviewer must verify that tests and evidence cover those behavior scenarios.

## When BDD Is Required

BDD scenarios are required when work is:

- user-facing
- workflow-facing
- agent collaboration related
- stateful
- approval/gate related
- evidence/redaction/export related
- integration-facing
- upstream-facing
- cross-module
- difficult to reverse

## Minimum Scenario Set

At minimum, define scenarios for:

- happy path
- failure path
- boundary case
- regression case
- security/redaction/export case when relevant
- approval or human-gate behavior when relevant
- handoff/communication behavior when relevant

## Example: ACS Sync

```text
Given Executor starts the first GA task of the day
When Executor prepares a Message To Reviewer
Then the message includes ACS local path, current ACS version, git pull result,
and the required ACS invocation sentence
```

## Example: Human Gate

```text
Given a task requires customer-visible report sending
When no approved HumanGate exists
Then report export is blocked and evidence is not exposed
```

## Reviewer Duties

Reviewer must check:

- Are the behavior scenarios written before or alongside implementation?
- Do tests map to the scenarios?
- Is each scenario observable through test output, evidence, or logs?
- Are failure and boundary paths covered?
- Do scenarios match the approved plan and project goal?
- Did implementation drift from the behavior scenarios?

Reviewer may reject a handoff if BDD scenarios are missing, vague, or not covered
by tests/evidence.

