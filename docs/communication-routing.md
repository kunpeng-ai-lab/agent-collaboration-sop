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

For every development or design task, the Reviewer must include:

```text
Please follow the ACS project standards for design/coding.
ACS project path: E:\workspace\agent-collaboration-sop
```

If the local machine uses another path, replace the path with the actual local
ACS clone path and record it in `docs/PROJECT_SOP.md`.

### Executor -> Reviewer

For every review request, the Executor must include:

```text
Please test and review according to ACS (E:\workspace\agent-collaboration-sop)
project standards.
```

If the local machine uses another path, replace the path with the actual local
ACS clone path and record it in `docs/PROJECT_SOP.md`.

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

If the Owner directly gives work to the Executor, the Executor must route it back
through the Reviewer unless the project SOP has an explicit emergency exception.

