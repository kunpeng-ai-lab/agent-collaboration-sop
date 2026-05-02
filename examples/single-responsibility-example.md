# Example: Single Responsibility Collaboration

## Setup

```text
Project Name: geo-agent
Project Short Name: GA
Owner Title: Owner
Executor Agent: Claude Code
Executor Short Name: CC
Reviewer Agent: Codex
Reviewer Short Name: CX
```

## Flow

1. Owner approves GA M4a scope.
2. CC implements Evidence and Redaction.
3. CC writes executor handoff.
4. CX reviews:
   - code
   - architecture
   - project goal fit
   - tests
   - redaction safety
   - evidence quality
5. CX finds two P1 issues.
6. CC fixes and resubmits.
7. CX approves.
8. CX writes Owner consensus report.
9. Owner approves entering M4b.

