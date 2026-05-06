# Executor Lessons

Redaction Status: reviewer-approved

## Core Lesson

Executor handoff must prove claims with evidence, not just state them.

In this case, the Executor initially reported green tests and zero product code
changes, but the evidence did not cover staged changes. After review, the
Executor diagnosed local dirty state, restored the baseline, and resubmitted
with stronger evidence.

## Good Executor Behavior

- Accepted review findings instead of defending a weak handoff.
- Found the root cause: local dirty state, not project baseline failure.
- Restored the official baseline rather than weakening tests.
- Updated evidence files and closure notes.

## Executor Improvements

- Always include staged and unstaged diff checks when claiming zero code changes.
- Do not update tests until the baseline source of failure is understood.
- Keep decision logs aligned with final outcome.
- Use evidence ledger as a proof record, not as a narrative afterthought.

## Reusable Handoff Rule

When saying "0 product code changes", include:

```text
git diff -- <product-path>
git diff --cached -- <product-path>
```

When saying "tests pass", include:

```text
<test command>
<test count>
<pass/fail count>
```

