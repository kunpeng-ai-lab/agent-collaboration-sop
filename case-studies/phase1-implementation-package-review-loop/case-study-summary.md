# ACS Case Study: Implementation Package Review Loop

Case ID: ACS-CS-20260506-IMPLEMENTATION-PACKAGE-REVIEW
Case Type: standard-case
Source Project: `<PROJECT>`
Source Phase: Phase 1 implementation package approval
Date: 2026-05-06
Prepared By: `<REVIEWER>`
Reviewed By: `<REVIEWER>`
Redaction Status: reviewer-approved

## Redaction Checklist

- [x] Owner, Executor, and Reviewer identities generalized where needed.
- [x] Private project names and repository URLs removed.
- [x] Local paths replaced with `<LOCAL_PATH>`.
- [x] Credentials, tokens, cookies, webhook URLs, and secrets removed.
- [x] Customer/commercial details generalized.
- [x] Screenshots omitted and replaced with shot descriptions.
- [x] The reusable lesson remains understandable.

## Mandatory Reviewer Redaction Approval

Redaction reviewed by:

- `<REVIEWER>`

Redaction review date:

- 2026-05-06

Redaction result:

- approved

Redaction evidence path:

- `<LOCAL_PATH>/case-studies/phase1-implementation-package-review-loop/`

Remaining disclosure risk:

- Low. The case uses generic project labels and omits raw screenshots, private
  paths, repo URLs, and customer details.

## Phase Goal

The phase was supposed to approve an implementation package before coding. The
Executor needed to define what pages/modules would change, how behavior would be
tested, how evidence would be captured, and which boundaries could not be
crossed.

The Reviewer had to prevent "looks approved in chat" from becoming "unsafe
execution plan in the repository."

## Approved Scope And Non-Scope

Scope:

- Repair/refactor existing product pages into an approved operator workflow.
- Keep product UI in valid UTF-8 Chinese.
- Add external JavaScript modules for interaction logic.
- Add behavior tests into the default test command.
- Add encoding checks, evidence ledgers, screenshots, and product validation.

Non-scope:

- No real agent integration.
- No real platform API calls.
- No backend modules.
- No customer report sending.
- No scoring engine.
- No role/permission redesign.
- No production deployment.

## Conversation Timeline

| Step | Actor | Summary | Evidence |
| --- | --- | --- | --- |
| 1 | Owner | Confirmed Phase 1 product decisions and requested implementation planning before coding. | Owner decision summary |
| 2 | Executor | Submitted an implementation package with BDD, page plan, file plan, tests, and evidence paths. | Executor handoff |
| 3 | Reviewer | Rejected because new tests were outside the default test glob, page sections risked duplication, inline logic conflicted with modular baseline, and product evidence covered too few pages. | Review findings |
| 4 | Executor | Revised the plan to include default test glob updates, external modules, 11-page validation, and a line-count stop condition. | Revised package |
| 5 | Reviewer | Rejected again after checking the actual file: target pages were not empty placeholders. Required current-state audit and preserve/repair/replace decisions. | Local file verification |
| 6 | Executor | Added current-state audit for each target page. | Revised package |
| 7 | Reviewer | Blocked because the plan proposed English UI copy as an encoding workaround. Escalated product-language decision to Owner. | Owner decision gate |
| 8 | Owner | Decided product UI must stay Chinese and the team must solve encoding correctly. | Owner decision |
| 9 | Executor | Added encoding governance, UTF-8 rules, and encoding evidence. | Revised package |
| 10 | Reviewer | Rejected fragile inline encoding checks and raw mojibake examples in formal docs. Required a dedicated check script and pattern IDs. | Review findings |
| 11 | Executor | Removed stale inline commands and raw garbled examples. | Final package |
| 12 | Reviewer | Approved the implementation package for coding, with hard stop conditions. | Final review |

## What Went Well

- The Reviewer checked the repository state instead of trusting the handoff.
- The Owner was only asked to decide genuine product questions, not routine
  implementation details.
- The team separated product UI language from documentation language.
- The plan moved from "add pages" to "repair/refactor current pages" after
  evidence showed the pages already existed.
- Encoding became an engineering gate, not a reason to abandon Chinese UI.

## What Went Wrong Or Almost Went Wrong

- The first implementation package proposed tests that would not run under the
  default command.
- The first page plan assumed empty placeholders even though existing sections
  had substantial content.
- The plan nearly reintroduced inline JavaScript after the project had recovered
  a modular baseline.
- "Fix to ASCII English" almost became a hidden product-language change.
- A handoff claimed a fragile command had been removed while the formal document
  still contained it.

## Reviewer Lessons

- Read the actual files and commands, not only the Executor summary.
- Compare handoff claims against the planning document.
- Treat default test command coverage as a hard gate.
- For UI work, review product language, page flow, and screenshot evidence.
- If a fix changes product behavior, escalate to Owner before approving.
- Do not allow "technical workaround" to silently become "product decision."

## Executor Lessons

- Implementation packages must be built from the current file snapshot.
- A "fixed" claim is incomplete unless the formal document also changed.
- New tests must be included in the default test gate.
- Page work should distinguish create, repair, refactor, and replace.
- Encoding gates should be implemented as scripts, not fragile shell one-liners.
- Product UI language must be explicit and Owner-approved.

## Evidence Pattern

What evidence was decisive?

- commands:
  - default test command and pass/fail count
  - source file scans for target IDs and script imports
  - pattern scans for stale inline commands and garbled fragments
- screenshots:
  - required for product-page validation, but omitted from this public case
- diffs:
  - planning document changes across revisions
- ledger:
  - reviewer report with each finding and closure status
- browser/page checks:
  - required after implementation for Chinese UI rendering

## ACS Rule Impact

This case reinforces these ACS rules:

- Default test command must include all new tests.
- Reviewer must verify handoff claims against files and commands.
- Product-facing UI changes require product-level validation.
- Product language is an Owner decision.
- Encoding/mojibake checks must be scripted, repeatable, and evidenced.
- Formal docs must not contain artifacts that their own rules forbid.
- A phase cannot enter coding until the implementation package is coherent.

## Future Team Checklist

- [ ] Does the default test command run the new tests?
- [ ] Are target pages created, repaired, refactored, or replaced?
- [ ] Does the plan preserve existing useful product structure?
- [ ] Does the plan change user-facing language?
- [ ] Are encoding checks automated and evidence-backed?
- [ ] Are screenshots planned for product-facing work?
- [ ] Does the formal document match the handoff summary?
- [ ] Are stop conditions explicit?
