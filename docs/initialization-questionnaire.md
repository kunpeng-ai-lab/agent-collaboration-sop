# Initialization Questionnaire

Before development, editing, review, deployment, or upstream work, the agents
must ask the Owner these questions and write the answers into
`docs/PROJECT_SOP.md`.

Do not skip this step.

## 1. Project Identity

Ask the Owner:

```text
1. What is the formal project name?
2. What short name should we use? Examples: GA, OWSL, ACS.
3. Is this project open source, closed source, or internal for now?
4. What is the most important short-term goal?
5. What is the long-term goal?
6. What is the repository URL?
7. What is the local project path?
8. What is the ACS local path? Example: E:\workspace\agent-collaboration-sop
```

## 2. Owner Title

Ask the Owner:

```text
1. How should we refer to you in docs and reports?
   Examples: Owner, Project Owner, Product Owner, Responsible Owner.
2. Which decisions must be confirmed by you?
```

Default Owner decision items:

- new phase start
- scope change
- deployment
- upstream PR
- public release
- customer-visible report
- commercial boundary
- credential or sensitive configuration use

## 3. Agent Identity And Short Names

Ask the Owner:

```text
1. Which agent is the Executor?
2. What is the Executor display name?
3. What is the Executor short name?
4. Which agent is the Reviewer?
5. What is the Reviewer display name?
6. What is the Reviewer short name?
```

Example:

```text
Executor Agent: Claude Code
Executor Short Name: CC

Reviewer Agent: Codex
Reviewer Short Name: CX
```

## 4. Communication Route

Ask the Owner:

```text
1. Are we using the default route?
   Executor -> Reviewer -> Owner
   Owner -> Reviewer -> Executor
2. Are there any emergency exceptions?
3. If an exception exists, who can approve it and how is it recorded?
```

Default answer should usually be:

```text
Use the default route. No direct Owner -> Executor execution orders and no
direct Executor -> Owner decision requests. Reviewer routes and consolidates.
```

## 5. Current Phase

Ask the Owner:

```text
1. What is the current phase called?
2. What is allowed in this phase?
3. What is explicitly not allowed in this phase?
4. What are the exit criteria?
5. Which tests or evidence are required?
```

## 6. Reviewer Authority

Ask the Owner:

```text
1. Can Reviewer block entry into the next phase?
2. Can Reviewer require more tests, docs, screenshots, or evidence?
3. Can Reviewer flag product goal, architecture, design, or scope drift?
4. Can Reviewer require a scope discussion package?
```

Recommended default answer: yes to all.

## 7. Mandatory ACS Invocation

Ask the Owner to confirm that every task message must include the ACS invocation.

Reviewer -> Executor development/design task:

```text
Please follow ACS project (<local ACS path>) standards for <design/coding>.
```

Executor -> Reviewer review request:

```text
Please test/review according to ACS project (<local ACS path>) standards.
```

Replace `<local ACS path>` with the real local ACS clone path. Replace
`<design/coding>` with the actual task type, such as `design`, `coding`, or
`design/coding`.

## 8. Write PROJECT_SOP

After confirmation, write all answers into:

```text
docs/PROJECT_SOP.md
```

Only then may execution or review begin.
