# Message ID Rules

Every formal ACS message must include a Message ID.

Message IDs help Owner, Reviewer, and Executor detect duplicate forwarding,
missed messages, stale handoffs, and repeated instructions.

## Required Format

Use local time:

```text
YYYYMMDDHHmm
```

Example:

```text
202605061145
```

If more than one formal message is sent in the same minute, add a short suffix:

```text
202605061145-R01
202605061145-E02
```

Suggested suffixes:

- `R` for Reviewer-originated message
- `E` for Executor-originated message
- `O` for Owner-originated message summarized by Reviewer

## Where To Put It

Add the Message ID near the top of every formal message:

```text
Message To Reviewer:
你好 <Reviewer>，我是 <Executor>。
Message ID: 202605061145-E01
```

or:

```text
Message To Executor:
你好 <Executor>，我是 <Reviewer>。
Message ID: 202605061145-R01
```

## Receiver Responsibility

Before acting on a formal ACS message, the receiver must check whether the
Message ID has already been processed in the current project/thread.

If duplicate:

- do not re-execute side-effectful work
- reply that the Message ID appears already processed
- ask for a new Message ID if the sender intends a new instruction

If missing:

- ask for a corrected message before substantive work starts

## Handoff And Review Records

Project handoff and review files should record the Message ID that triggered the
work or review.

Recommended fields:

```text
Message ID:
Responds To Message ID:
```

Use `Responds To Message ID` when a review, correction, or closure answers a
previous message.

## Redline

No Message ID means the formal ACS message is incomplete.

Duplicate Message IDs must be treated as possible duplicate forwarding until
verified otherwise.

