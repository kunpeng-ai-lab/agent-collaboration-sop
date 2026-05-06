# ACS File-First Handoff Rules

Long handoffs are not reliable when copied through desktop chat clients. Even
valid fenced code blocks or ACS message envelopes may lose copy buttons, render
partially, or become hard for the Owner to forward.

ACS therefore uses a file-first rule for long or formal project handoffs.

## Rule

If a handoff, design package, review request, closure note, or evidence summary
is longer than a short screenful, the Executor must write the full content to a
project file and send only a short chat notification.

Recommended paths:

- `docs/handoffs/<message-id>-executor-handoff.md`
- `docs/planning/<phase>-design-package.md`
- `reviews/<phase>/executor-handoff.md`
- `reports/<phase>-closure.md`

The chat message should include:

1. Message ID
2. Responds To Message ID
3. ACS version
4. Handoff file path
5. One short summary
6. Exact review request
7. ACS invocation sentence

## Chat Template

Use this short format in chat:

```text
<<<ACS_MESSAGE_BEGIN>>>
Message To Reviewer:
你好 <Reviewer>，我是 <Executor>。
Message ID: <YYYYMMDDHHmm-E01>
Responds To Message ID: <YYYYMMDDHHmm-R01>
ACS 当前版本: <short-sha>
已执行 git pull origin main: yes / no

完整 handoff 已写入:
<project-relative-or-absolute-path>

摘要:
- <one to five concise bullets>

请审核该文件，不以聊天正文作为正式交付物。

请按照 ACS 项目（<ACS 本地路径>）规范进行（测试/审核）。
<<<ACS_MESSAGE_END>>>
```

## Reviewer Behavior

The Reviewer must review the file, not the shortened chat body. The review
report must cite:

- the handoff file path
- the Message ID
- the evidence ledger path
- any screenshots or product validation files used

## Owner Forwarding

The Owner should not be asked to copy long handoff content. The Owner only needs
to forward the short path-based notification. Agents sharing the same machine or
repository must read the file directly.

If agents are on different machines, the Executor must commit/push the handoff
file or attach/export the file through an approved transfer channel before
requesting review.

