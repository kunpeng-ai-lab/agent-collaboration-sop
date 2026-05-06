# Communication Routing And Mandatory ACS Invocation

This document defines the long-term communication route for Agent Collaboration
SOP projects. It is intentionally strict: the goal is to keep one clear review
authority between the Owner and the Executor.

See also:

- `docs/acs-sync-rules.md`

## Long-Term Communication Flow

### 1. Executor -> Owner

The Executor does not communicate directly with the Owner during normal project
execution.

- The Executor talks to the Reviewer.
- If the Executor wants to say something to the Owner, the Executor writes it to
  the Reviewer.
- The Owner forwards Executor messages to the Reviewer for evaluation and
  consolidation.

### 2. Reviewer -> Owner

The Reviewer communicates directly with the Owner.

- If a decision, approval, or clarification is needed, the Reviewer asks the
  Owner.
- After the Owner responds, the Reviewer writes a consolidated message that
  includes the Owner's decision and sends it to the Executor.
- The Owner may forward that Reviewer message to the Executor.

### 3. Owner -> Executor

The Owner does not bypass the Reviewer to give direct execution instructions.

- The Owner tells the Reviewer what needs to be done.
- The Reviewer discusses with the Executor when needed.
- The Reviewer then sends the Executor an instruction package that includes
  Owner intent, scope, constraints, and ACS requirements.

## Mandatory ACS Sync

Before accepting or sending a task, apply `docs/acs-sync-rules.md`.

Minimum sync command:

```powershell
cd <ACS 本地路径>
git pull origin main
git rev-parse --short HEAD
```

The current message or handoff must include ACS local path, ACS version, and
whether `git pull origin main` was executed.

## Mandatory ACS Invocation

Every development, design, testing, or review handoff must explicitly invoke the
ACS rules and project path.

### Reviewer -> Executor

For every development, design, or coding task, the Reviewer must include:

```text
请遵循 ACS 项目（<ACS 本地路径>）规范进行（<设计/编码>）。
```

Replace `<ACS 本地路径>` with the actual local ACS clone path. Replace
`<设计/编码>` with the actual task type, such as `设计`, `编码`, or
`设计/编码`. Record the resolved path in `docs/PROJECT_SOP.md`.

### Executor -> Reviewer

For every testing, review, acknowledgement, blocked note, or handoff, the
Executor must include:

```text
请按照 ACS 项目（<ACS 本地路径>）规范进行（<测试/审核>）。
```

Replace `<ACS 本地路径>` with the actual local ACS clone path. Replace
`<测试/审核>` with the actual task type, such as `测试`, `审核`, or
`测试/审核`. Record the resolved path in `docs/PROJECT_SOP.md`.

## Message Format

All Owner-forwarded messages that should be copied to another agent must be
wrapped in a fenced code block.

If the relay path cannot reliably preserve fenced code blocks, use the fallback
envelope defined in `docs/message-envelope-rules.md`:

```text
<<<ACS_MESSAGE_BEGIN>>>
Message To Reviewer:
你好 <Reviewer>，我是 <Executor>。
Message ID: <YYYYMMDDHHmm-E01>
Responds To Message ID: <YYYYMMDDHHmm-R01>

<message body>

请按照 ACS 项目（<ACS 本地路径>）规范进行（测试/审核）。
<<<ACS_MESSAGE_END>>>
```

The begin marker must be the first line, the end marker must be the last line,
and no text may appear outside the envelope.

The Executor must explicitly produce a `Message To Reviewer` section whenever a
task is acknowledged, completed, blocked, or ready for review.

The entire `Message To Reviewer` must be wrapped in one fenced code block so the
Owner can copy it without formatting drift.

The first line of the message body must identify recipient and sender:

```text
你好 <Reviewer>，我是 <Executor>。
```

Minimum Executor acknowledgement:

````text
```text
Message To Reviewer:
你好 Codex，我是 CC。

我已收到并接受 ACS 路由和规范更新要求。
ACS 本地路径：<ACS 本地路径>
ACS 当前版本：<git rev-parse --short HEAD>
已执行：git pull origin main
当前角色：Executor
Reviewer：Codex
下一步状态：<等待任务 / 执行中 / 提交审核 / 阻塞>

请按照 ACS 项目（<ACS 本地路径>）规范进行（测试/审核）。
```
````

A screen-only confirmation, non-fenced Markdown list, or general note is not a
closed loop.

## Updating Older Agent Rules

If an agent already stored an older ACS wording in long-term memory, project
rules, or local prompts, the Reviewer must send an explicit update instruction.
The instruction must be wrapped in a fenced code block and must require replacing
old ACS wording with:

```text
1. 每天 06:00 或每天第一次任务前同步 ACS；Owner/Reviewer 明确要求时立即同步。
2. 同步命令：cd <ACS 本地路径>; git pull origin main; git rev-parse --short HEAD。
3. 请遵循 ACS 项目（<ACS 本地路径>）规范进行（<设计/编码>）。
4. 请按照 ACS 项目（<ACS 本地路径>）规范进行（<测试/审核>）。
5. Executor 给 Reviewer 的确认、阻塞说明、handoff、review 请求都必须整体包裹在代码块中。
6. Message To Reviewer 正文第一句必须是：你好 <Reviewer>，我是 <Executor>。
7. 回执必须报告 ACS 当前版本。
```

## Required Project-Level Fields

Each project using ACS must record:

- ACS repository URL
- local ACS path
- Owner title
- Executor name and short name
- Reviewer name and short name
- whether communication is single-responsibility or cross-review
- whether the Owner has approved any exception to the routing rules

## Redline

If ACS sync evidence is missing, the receiving agent must ask for correction
before substantive work.

If the mandatory ACS invocation is missing from a task handoff, the receiving
agent must ask for correction before starting substantive work.

If the Executor does not produce a message addressed to the Reviewer, the loop is
not closed and the Reviewer must ask for a corrected acknowledgement or handoff.

If the Executor's acknowledgement is not wrapped as a fenced code block, the loop
is not closed.

If fenced code blocks are not preserved by the client, the Executor must use the
ACS fallback envelope. Missing `<<<ACS_MESSAGE_BEGIN>>>`, missing
`<<<ACS_MESSAGE_END>>>`, or extra text outside the envelope means the loop is not
closed.

If the Executor's `Message To Reviewer` does not start with
`你好 <Reviewer>，我是 <Executor>。`, the loop is not closed.

If the Owner directly gives work to the Executor, the Executor must route it back
through the Reviewer unless the project SOP has an explicit emergency exception.
