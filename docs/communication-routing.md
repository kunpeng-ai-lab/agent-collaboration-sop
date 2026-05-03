# Communication Routing And Mandatory ACS Invocation

This document defines the long-term communication route for Agent Collaboration
SOP projects. It is intentionally strict: the goal is to keep one clear review
authority between the Owner and the Executor.

## Long-Term Communication Flow

### 1. Executor -> Owner

The Executor does not communicate directly with the Owner during normal project
execution.

- The Executor talks to the Reviewer.
- If the Executor wants to say something to the Owner, the Executor writes it to
  the Reviewer.
- The Owner forwards Executor messages to the Reviewer for evaluation and
  consolidation.

Reason: the Reviewer must protect scope, quality, traceability, and project
direction before any message becomes an Owner decision request.

### 2. Reviewer -> Owner

The Reviewer communicates directly with the Owner.

- If a decision, approval, or clarification is needed, the Reviewer asks the
  Owner.
- After the Owner responds, the Reviewer writes a consolidated message that
  includes the Owner's decision and sends it to the Executor.
- The Owner may forward that Reviewer message to the Executor.

Reason: Owner decisions should arrive at the Executor with context, constraints,
quality requirements, and review expectations attached.

### 3. Owner -> Executor

The Owner does not bypass the Reviewer to give direct execution instructions.

- The Owner tells the Reviewer what needs to be done.
- The Reviewer discusses with the Executor when needed.
- The Reviewer then sends the Executor an instruction package that includes
  Owner intent, scope, constraints, and ACS requirements.

Reason: this prevents accidental scope expansion, unreviewed direction changes,
and "Owner said so" implementation without a design/review trail.

## Mandatory ACS Invocation

Every development, design, testing, or review handoff must explicitly invoke the
ACS rules and project path.

### Reviewer -> Executor

For every development, design, or coding task, the Reviewer must include:

```text
请遵循 ACS 项目（<ACS 本地路径>）规范进行（<设计/编码>）。
```

Replace `<ACS 本地路径>` with the actual local ACS clone path. Replace
`<设计/编码>` with the actual task type, such as `设计`, `编码`, or
`设计/编码`. Record the resolved path in `docs/PROJECT_SOP.md`.

### Executor -> Reviewer

For every testing, review, acknowledgement, blocked note, or handoff, the
Executor must include:

```text
请按照 ACS 项目（<ACS 本地路径>）规范进行（<测试/审核>）。
```

Replace `<ACS 本地路径>` with the actual local ACS clone path. Replace
`<测试/审核>` with the actual task type, such as `测试`, `审核`, or
`测试/审核`. Record the resolved path in `docs/PROJECT_SOP.md`.

The Executor must explicitly produce a `Message To Reviewer` section whenever a
task is acknowledged, completed, blocked, or ready for review. A screen-only
confirmation or general note is not a closed loop.

Minimum Executor acknowledgement:

```text
Message To Reviewer:
I have received and accepted the ACS routing/update requirements.
ACS local path: <ACS 本地路径>
Current role: Executor
Reviewer: <Reviewer name>
Next action: <waiting / implementing / handing off / blocked>
请按照 ACS 项目（<ACS 本地路径>）规范进行（<测试/审核>）。
```

## Updating Older Agent Rules

If an agent already stored an older ACS wording in long-term memory, project
rules, or local prompts, the Reviewer must send an explicit update instruction:

```text
Please replace any older ACS wording in your memory/rules with the latest ACS
templates:
1. 请遵循 ACS 项目（<ACS 本地路径>）规范进行（<设计/编码>）。
2. 请按照 ACS 项目（<ACS 本地路径>）规范进行（<测试/审核>）。
Use the actual ACS local path for this machine.
Executor acknowledgements and handoffs must include a Message To Reviewer section.
```

## Required Project-Level Fields

Each project using ACS must record:

- ACS repository URL
- local ACS path
- Owner title
- Executor name and short name
- Reviewer name and short name
- whether communication is single-responsibility or cross-review
- whether the Owner has approved any exception to the routing rules

## Redline

If the mandatory ACS invocation is missing from a task handoff, the receiving
agent must ask for correction before starting substantive work.

If the Executor does not produce a message addressed to the Reviewer, the loop is
not closed and the Reviewer must ask for a corrected acknowledgement or handoff.

If the Owner directly gives work to the Executor, the Executor must route it back
through the Reviewer unless the project SOP has an explicit emergency exception.
