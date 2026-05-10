# ACS Public Anti-Pattern Library

Status: public-safe draft
Redaction status: sanitized

Anti-patterns are not blame records. They are reusable warnings for teams that
use AI agents in engineering workflows.

## Anti-Pattern 1: Agent Self-Approval

### What It Looks Like

The Executor edits code, runs tests, writes a confident summary, and declares
the task done without independent review.

### Why It Is Dangerous

The same agent that made the assumptions also validates those assumptions.
Scope drift, missing evidence, weak tests, and product misalignment can all be
missed.

### ACS Prevention

Separate Executor and Reviewer roles. Reviewer checks command, evidence,
product, architecture, security/redaction, and release gates before Owner
approval.

## Anti-Pattern 2: Green Tests Treated As Approval

### What It Looks Like

The handoff says "tests passed" and the task is treated as complete.

### Why It Is Dangerous

Tests can pass while:

- the default test command omits new tests;
- staged diffs hide unapproved changes;
- UI pages were never opened;
- evidence screenshots are missing;
- the work violates the approved product direction.

### ACS Prevention

Reviewer records a report with four gates: command, evidence, product, and
architecture. Green tests are one input, not the decision.

## Anti-Pattern 3: Evidence Exists Only In Chat

### What It Looks Like

Important commands, decisions, screenshots, and review notes are scattered
across chat messages.

### Why It Is Dangerous

Chat context can be compacted, lost, copied incompletely, or separated from the
repository. Future agents cannot reconstruct the phase.

### ACS Prevention

Use file-first handoffs, evidence ledgers, reviewer reports, and owner
consensus reports. Chat should point to files, not replace them.

## Anti-Pattern 4: Handoff Says Fixed, Formal Document Still Says Otherwise

### What It Looks Like

The Executor says a finding is fixed, but the design package still contains the
old command, old scope, old version, or stale instruction.

### Why It Is Dangerous

Future implementation follows the document, not the chat summary. The same bug
can be reintroduced immediately.

### ACS Prevention

Reviewer searches the formal files for stale wording and blocks until the
document and handoff match.

## Anti-Pattern 5: Product-Language Drift Hidden As A Technical Fix

### What It Looks Like

An agent proposes changing user-facing language to avoid encoding or rendering
problems.

### Why It Is Dangerous

A technical workaround becomes a product decision without Owner approval.

### ACS Prevention

Reviewer escalates product-language decisions to Owner. Encoding must be solved
as an engineering issue when the product language is already approved.

## Anti-Pattern 6: Screenshot-Free UI Approval

### What It Looks Like

The Executor changes UI, reports tests passed, and asks for approval without
page screenshots or browser validation.

### Why It Is Dangerous

Automated tests can miss layout crowding, invisible controls, confusing labels,
or broken visual hierarchy.

### ACS Prevention

Product-facing work requires page/workflow validation and screenshot evidence.

## Anti-Pattern 7: Unsafe Public Output

### What It Looks Like

An agent prepares a case study, public post, PR, or customer-facing report using
raw project names, paths, screenshots, or business details.

### Why It Is Dangerous

The technical lesson may expose private customer data, private repositories,
credentials, local machine paths, or unreleased strategy.

### ACS Prevention

Case-study redaction is a blocking Reviewer gate. Public artifacts must use
placeholders and redacted summaries.

