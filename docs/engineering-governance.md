# Engineering Governance Rules

These rules are mandatory for projects using Agent Collaboration SOP.

They are designed for human maintainability, traceability, and Owner-auditable
evidence chains.

## 1. Human-Debuggable Code

Important code and module methods must be understandable by a human engineer.

Required:

- Important modules must have a short module-level comment explaining purpose,
  boundaries, and non-goals.
- Important exported functions/classes must have comments describing:
  - what the function does
  - important inputs and outputs
  - side effects, if any
  - failure behavior
  - security or data-sensitivity assumptions
- Complex decisions must be documented near the code, not only in chat.
- Comments must explain why, not repeat obvious syntax.

Not required:

- Comments on every trivial line.
- Decorative comments.
- Comments that claim behavior not covered by tests or verification.

Reviewer must check:

- can a human engineer debug the module without reading the entire chat history?
- are important safety, state, retry, redaction, approval, or export rules visible
  in code comments or nearby docs?
- are comments still truthful after implementation?

## 2. Traceable Verification And Review

Any testing, verification, review, deployment, upstream PR, or customer-visible
work must leave a traceable record.

Required records:

- command run
- exact result
- date/time when useful
- environment or branch when relevant
- screenshots for UI, GitHub, CI, deploy, PR, forum, blog, customer-visible, or
  production-facing evidence
- reviewer decision
- Owner approval when required

Storage:

- use the project evidence ledger
- store screenshots under an evidence directory
- link reports, commits, PRs, issues, CI, deploys, or public pages

Rule:

```text
No evidence ledger entry -> not accepted as verified.
No screenshot for visual/public/remote state -> not accepted as traceable.
```

## 3. Development Package Before Coding

Every non-trivial development unit must start from an approved development
package.

The package must include:

- plan
- design notes
- technical/architecture research
- module boundary and decoupling notes
- test cases
- constraints and non-scope
- minimal-change strategy
- documentation impact
- evidence plan
- rollback or recovery plan when relevant

The executor prepares it. The reviewer reviews it before implementation when the
change is high-risk, cross-module, customer-visible, upstream-facing, or
architecture-affecting.

Owner approval is required when the package changes phase scope, public output,
commercial boundary, deployment, upstream PR, credentials, or customer-visible
delivery.

See also:

- `docs/technical-design-rules.md`

## 4. Minimal Change Rule

Changes must be scoped to the approved unit of work.

Required:

- prefer the smallest change that satisfies the approved design
- do not mix unrelated refactors with feature work
- do not rewrite neighboring modules unless the plan explicitly says so
- document any unavoidable spillover

Reviewer must reject:

- hidden scope expansion
- opportunistic refactors
- broad rewrites without Owner-approved design
- tests that pass while architecture or product goals drift

## 5. Reviewer Audit Duty

Reviewer must audit more than code.

Reviewer must check:

- project goal alignment
- design alignment
- architecture boundaries
- module decoupling and dependency direction
- whether technical and architecture research is sufficient
- engineering structure
- comments and human-debuggability
- test quality
- verification evidence
- screenshot/evidence ledger completeness
- security and redaction
- release/deploy/upstream/customer risk
- whether Owner approval is required

Reviewer output must be traceable:

- pass or needs changes
- findings with file paths and line numbers when possible
- verification commands and results
- evidence ledger links
- Owner decision items

## 6. Owner Evidence Chain

Owner decisions must be backed by a visible evidence chain.

Before asking Owner to approve next phase, release, deployment, upstream PR, or
customer-visible output, reviewer must provide:

- what changed
- why it matters
- what was verified
- where the evidence is stored
- what risks remain
- what exact decision is requested

Owner approval must be recorded in the ledger or project decision log.
