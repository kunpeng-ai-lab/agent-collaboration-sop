# ACS Public Material Pack

Status: public-safe draft
Redaction status: sanitized, no private customer or repository data
Audience: engineering leaders, AI agent users, maintainers, open-source
contributors, internal platform teams

## 1. Design Background: Why ACS Exists

ACS exists because AI agent engineering work fails in ways that normal "green
tests" cannot catch.

In multi-agent engineering, one agent often acts as the Executor: it reads the
task, edits files, runs commands, and writes a handoff. Another agent may act as
Reviewer, but without a protocol the review can collapse into a shallow replay
of the Executor's claims. The Owner then receives a confident summary but not a
trustworthy decision trail.

ACS turns that loose chat workflow into a controlled collaboration system:

- Owner makes final decisions about goals, scope, releases, public output, and
  business boundaries.
- Executor designs, implements, self-tests, and writes evidence-backed handoffs.
- Reviewer independently checks commands, evidence, architecture, product goal
  alignment, risk, redaction, and release readiness before reporting consensus
  to Owner.

The core problem ACS solves is not "agents forget to run tests." It is deeper:

- agents can self-approve their own work;
- tests can pass while the work violates scope;
- evidence can exist in chat but disappear from the repository;
- Owner decisions can be lost after context compaction;
- handoffs can say "fixed" while the formal design file still contains the old
  instruction;
- UI, deployment, upstream PR, and customer-visible work can be approved without
  screenshots or ledger proof.

ACS makes these failure modes explicit and repeatable. It requires structured
messages, unique Message IDs, file-first handoffs, evidence ledgers, reviewer
reports, product validation, and redaction gates.

## 2. Public Positioning

One-line positioning:

> ACS is a vendor-neutral SOP for making Owner / Executor / Reviewer AI-agent
> engineering collaboration auditable, reviewable, and reusable.

Short positioning:

> ACS helps teams stop treating AI agent work as a chat transcript. It turns
> agent execution into a phase-based engineering workflow with role separation,
> evidence ledgers, reviewer gates, Owner decisions, and reusable case studies.

Long positioning:

> ACS is for teams that already use AI coding agents but need stronger control
> over scope, evidence, review, and release decisions. It separates the Executor
> who performs work from the Reviewer who checks more than green tests. The
> Owner remains the final decision maker for goals, business boundaries,
> production release, upstream PRs, and public/customer-visible output. Over
> time, ACS turns each collaboration loop into a reusable engineering case or
> anti-pattern, so teams can improve their agent process instead of repeating
> the same mistakes in new chats.

## 3. Main Website Topic Angles

### Angle A: "Green Tests Are Evidence, Not Approval"

Use when introducing ACS to engineering teams.

Core idea:

- Passing tests prove only that a chosen command passed.
- They do not prove scope compliance, product alignment, git state, screenshot
  evidence, release safety, or customer-visible correctness.
- ACS requires Reviewer to check evidence gates before Owner approval.

Suggested title:

- Green Tests Are Evidence, Not Approval: Why AI Agent Work Needs a Reviewer
  Protocol

### Angle B: "From Chat Logs To Evidence Ledgers"

Use when explaining long-term knowledge accumulation.

Core idea:

- Chat history is fragile.
- Evidence ledgers preserve what changed, how it was verified, which screenshots
  exist, which decisions were made, and what risk remains.
- Case studies and anti-patterns convert phase closures into reusable learning.

Suggested title:

- From Chat Logs To Evidence Ledgers: Building A Long-Term AI Agent Engineering
  Case Library

### Angle C: "Owner / Executor / Reviewer Is A Control System"

Use when discussing governance.

Core idea:

- Owner is not a passive requester.
- Executor is not allowed to self-approve.
- Reviewer is not just a test runner.
- The three roles create a control loop for scope, evidence, decisions, and
  release readiness.

Suggested title:

- Owner, Executor, Reviewer: A Practical Control Loop For AI Agent Engineering

### Angle D: "Anti-Patterns Are Productive Assets"

Use when recruiting community contributors.

Core idea:

- The most useful cases often begin as mistakes.
- ACS stores anti-patterns without blame: hidden staged diffs, document drift,
  missing screenshots, stale decisions, unsafe public output, and evidence gaps.
- The goal is to teach prevention checklists.

Suggested title:

- Why We Store AI Agent Anti-Patterns: Turning Failures Into Reusable Team
  Memory

## 4. Matrix Distribution Snippets

### Short Post 1

AI coding agents can pass tests and still fail the job.

They may drift from scope, skip screenshot evidence, forget Owner decisions, or
claim a handoff is fixed while the design file still says otherwise.

ACS separates Owner / Executor / Reviewer so agent work becomes auditable:
commands, evidence ledgers, reviewer reports, and redacted case studies.

### Short Post 2

Our rule for AI agent engineering:

Green tests are evidence, not approval.

Approval requires scope checks, architecture review, product validation,
screenshot/evidence proof, redaction review, and an Owner decision trail.

That is what ACS standardizes.

### Short Post 3

Chat is not a durable engineering record.

ACS moves AI agent collaboration into files:

- Executor handoff
- Reviewer report
- Evidence ledger
- Owner consensus report
- Case study
- Anti-pattern review

The result is not just one task completed. It is a reusable collaboration
memory.

## 5. Community Contribution Message

We welcome sanitized ACS-style cases from teams using AI agents in real
engineering workflows.

Useful contributions include:

- Executor / Reviewer collaboration loops;
- code review cases where tests passed but the design was wrong;
- upstream PR or issue workflows involving agent-generated changes;
- release or deployment evidence ledgers;
- anti-patterns such as hidden diffs, missing screenshots, stale handoffs, or
  self-approval;
- reviewer checklists that caught product, architecture, security, or redaction
  risks;
- examples of how Owner decisions changed the phase boundary.

Before contributing, remove customer names, private repositories, local paths,
tokens, credentials, unreleased commercial information, and raw private
screenshots. Keep the lesson, remove the sensitive details.

## 6. Redaction Statement For Public Pages

All public ACS case materials are sanitized. Case studies preserve the decision
flow, evidence pattern, reviewer reasoning, and reusable lesson, while removing
customer names, private repositories, local paths, credentials, contact details,
commercial terms, and unreleased project information.

