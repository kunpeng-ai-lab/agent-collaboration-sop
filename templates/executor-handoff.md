# Executor Handoff

Project:
Project Short Name:
Phase:
Executor Agent:
Executor Short Name:
Date:

## Summary

What was completed:

- 

Why:

- 

## ACS Sync Evidence

ACS local path:
ACS current version:
Executed `git pull origin main`: yes / no
Sync failure reason, if any:

## Development Package

Plan:

- 

Design notes:

- 

Technical/architecture research:

- 

Behavior scenarios:

```text
Given <context>
When <action>
Then <expected behavior>
```

Additional scenarios:

| Scenario | Given | When | Then | Test/Evidence |
| --- | --- | --- | --- | --- |
| happy path | | | | |
| failure path | | | | |
| boundary case | | | | |
| regression case | | | | |
| security/redaction/export case | | | | |

Options considered:

| Option | Pros | Cons | Decision |
| --- | --- | --- | --- |
| | | | |

Module boundaries:

- 

Dependency direction:

- 

Data flow:

- 

Failure behavior:

- 

Test cases:

- 

Test coverage matrix:

| Path | Test | Evidence |
| --- | --- | --- |
| happy path | | |
| failure path | | |
| boundary case | | |
| regression case | | |
| security/redaction/export case | | |

Constraints:

- 

Explicit non-scope:

- 

Minimal-change strategy:

- 

Documentation impact:

- 

Evidence plan:

- 

## Changed Files

- 

## Comments And Human Debuggability

Important modules/methods touched:

- 

Comments added or updated:

- 

Areas intentionally left uncommented because they are trivial:

- 

## Verification

Commands run:

```text

```

Results:

```text

```

Evidence ledger entry:

- 

Screenshots:

- 

## Scope Notes

In scope:

- 

Not included:

- 

## Risks

- 

## Message To Reviewer

The Executor must explicitly address the Reviewer. A screen-only confirmation,
non-fenced Markdown list, or general note is not enough. The whole message must
be wrapped in one fenced code block. The first sentence must identify recipient
and sender.

```text
Message To Reviewer:
你好 <Reviewer>，我是 <Executor>。

<write the acknowledgement, completion note, blocked reason, or review request here>

ACS 当前版本：<git rev-parse --short HEAD>

请按照 ACS 项目（<ACS 本地路径>）规范进行（<测试/审核>）。
```

Reviewer should focus on:

1. 
2. 
3. 

## Owner Decisions Needed

- none
