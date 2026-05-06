# ACS Message Envelope Rules

ACS messages are often copied through chat clients, IDE panels, desktop apps,
and browser renderers. Some clients may strip or partially render Markdown
fenced code blocks. To keep Owner-forwarded messages copyable and auditable,
ACS defines two valid envelope formats.

## Preferred Format: Fenced Code Block

Use one single fenced code block when the client preserves Markdown fences
reliably.

````text
```text
Message To Reviewer:
你好 Codex，我是 CC。
Message ID: 202605061145-E01
Responds To Message ID: 202605061140-R01
ACS 当前版本: <short-sha>
已执行 git pull origin main: yes

<message body>

请按照 ACS 项目（<ACS 本地路径>）规范进行（测试/审核）。
```
````

Rules:

1. No text may appear outside the fenced code block.
2. The message must start with `Message To Reviewer:`.
3. The next line must be `你好 <Reviewer>，我是 <Executor>。`.
4. `Message ID` and `Responds To Message ID` must be near the top.
5. The ACS invocation sentence must be included near the end.

## Fallback Format: ACS Message Envelope

If the chat client, desktop app, browser renderer, or relay path cannot reliably
preserve Markdown fenced code blocks, use the ACS message envelope instead.

```text
<<<ACS_MESSAGE_BEGIN>>>
Message To Reviewer:
你好 Codex，我是 CC。
Message ID: 202605061145-E01
Responds To Message ID: 202605061140-R01
ACS 当前版本: <short-sha>
已执行 git pull origin main: yes

<message body>

请按照 ACS 项目（<ACS 本地路径>）规范进行（测试/审核）。
<<<ACS_MESSAGE_END>>>
```

Rules:

1. `<<<ACS_MESSAGE_BEGIN>>>` must be the first line.
2. `<<<ACS_MESSAGE_END>>>` must be the last line.
3. No text, Markdown table, screenshot-only note, or `Updated todos` text may
   appear outside the envelope.
4. The body rules are the same as the fenced code block format.
5. The receiver must reject a formal ACS message if either boundary marker is
   missing or if extra text appears outside the envelope.

## When To Use The Fallback

Use the fallback envelope when any of these happen:

- the fenced code block is truncated
- the closing fence is missing
- the app renders part of the message outside the block
- Markdown tables or nested code fences break copyability
- the Owner reports that the message cannot be copied as one complete block

## Simplicity Rule

For long handoffs, prefer plain numbered sections and bullet lists. Avoid complex
Markdown tables, nested fences, and decorative separators. They are easy for
desktop clients to render incorrectly and make evidence traceability worse.

## Receiver Behavior

If a formal ACS message is not wrapped in one valid format, the receiver must not
review the substantive content. Ask for a corrected resend with a new Message ID
or with a correction Message ID that clearly responds to the rejected one.
