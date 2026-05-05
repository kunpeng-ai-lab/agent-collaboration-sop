# Technical Design Rules

These rules define the minimum design quality bar before coding starts.

They apply to non-trivial code, architecture, module, API, workflow, agent,
integration, storage, reporting, deployment, or automation changes.

## 1. Design Before Implementation

Executor must prepare a design note before implementation when the change is:

- cross-module
- architecture-affecting
- integration-facing
- stateful
- security-sensitive
- customer-visible
- upstream-facing
- difficult to reverse

The design note must be reviewed before implementation unless Owner explicitly
approves a smaller spike/prototype.

## 2. Required Design Inputs

The design note must include:

- goal and non-goal
- user/product problem
- Given / When / Then behavior scenarios
- current architecture context
- researched options
- recommended option and why
- module boundaries
- dependency direction
- data flow
- state ownership
- failure behavior
- security/redaction considerations
- test strategy
- migration or rollback plan when relevant

Research does not need to be long, but it must be real. Examples:

- inspect existing code patterns
- inspect framework/library docs
- compare 2-3 implementation options
- check related issues/PRs
- check operational constraints

## 3. Modular Design And Decoupling

Modules should be designed so they can be understood, tested, and replaced.

Required:

- each module has one clear responsibility
- dependencies point inward toward stable interfaces, not outward toward callers
- runtime-specific logic is behind adapters/profiles
- side effects are isolated at boundaries
- pure logic is kept separate from I/O when practical
- schema/contracts are explicit when data crosses module boundaries
- state ownership is clear

Reviewer must reject designs where:

- one module owns unrelated responsibilities
- business rules, I/O, persistence, and formatting are tangled without reason
- new code reaches across layers instead of using the agreed interface
- implementation bypasses approved gates, adapters, schemas, or guards

## 4. Stability And Failure Design

Every important design must state how it fails.

Required:

- what happens on bad input
- what happens on timeout
- what happens on partial failure
- what happens on retry exhaustion
- what happens if dependency/runtime/platform is unavailable
- whether the system fails open or fails closed

Default for safety-sensitive work:

```text
fail closed
```

## 5. Design Verification

Reviewer must verify design quality, not only implementation.

Reviewer must check:

- does the design match approved plan and project goals?
- are module boundaries reasonable?
- is decoupling strong enough for planned extension?
- are dependencies pointed in the right direction?
- is failure behavior explicit?
- are safety gates preserved?
- is the test strategy aligned with design risks?
- do behavior scenarios cover happy, failure, boundary, and regression paths?
- can a human engineer debug and maintain it?

Reviewer may require design changes even when code works and tests pass.

## 6. Design Evidence

Design review must be traceable.

Store at least one of:

- design note
- ADR
- architecture sketch
- interface contract
- decision log entry
- reviewer report section

Owner approval must reference the design evidence when the change affects scope,
architecture, public API, production, upstream, or customer-visible output.
