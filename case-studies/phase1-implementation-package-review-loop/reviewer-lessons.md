# Reviewer Lessons

Redaction Status: reviewer-approved

## 1. Review The Executable Gate

Do not accept "tests added" unless the tests run under the agreed command.

Questions:

- What is the default test command?
- Do the new tests match its glob?
- Does the handoff record the command output?

## 2. Verify Current State Before Reviewing The Plan

Plans often describe intended targets incorrectly. The Reviewer should inspect
the current files before deciding whether an implementation strategy is safe.

Questions:

- Does the target file already contain content?
- Is the plan adding, replacing, or repairing?
- Are IDs, routes, tabs, or selectors duplicated?

## 3. Separate Product Decisions From Technical Workarounds

When the Executor proposes a "simple technical fix" that changes what the user
sees, the Reviewer should escalate to Owner.

Examples:

- changing UI language
- changing workflow order
- removing a page state
- hiding user-facing warnings

## 4. Check Handoff Against Formal Artifact

Executor chat can be accurate in intent but stale in files. The Reviewer must
open the formal document and search for contradictions.

Checks:

- Does the document version match the handoff?
- Are old command blocks removed?
- Do scope and non-scope still agree?
- Do evidence paths match the actual plan?

## 5. Product Validation Is Not Optional For UI Work

For UI/prototype tasks, command tests are not enough. Reviewer should require:

- page walkthrough
- screenshots
- no console errors
- role-specific view checks
- text readability
- empty state checks
- adjacent page regression checks

## 6. Encoding Is A Gate

For multilingual or Chinese product work:

- require UTF-8 file rules
- require an encoding check script
- require browser rendering evidence
- reject raw mojibake in formal docs
- keep product language Owner-approved
