# Case Study Redaction Rules

ACS case studies and anti-patterns are meant to teach agent behavior, not expose
private project data.

Use these rules before adding any phase conversation, review excerpt, evidence
summary, screenshot, or failure analysis to `case-studies/` or
`anti-patterns/`.

## Redaction Goals

Every published or reusable ACS case must preserve:

- decision context
- communication flow
- reviewer reasoning
- executor mistakes and corrections
- evidence patterns
- the reusable lesson

Every published or reusable ACS case must remove or generalize:

- customer names
- private project names
- private repository URLs
- local usernames and absolute paths
- tokens, cookies, API keys, session IDs, webhook URLs, and credentials
- private emails, phone numbers, and contact details
- production domains when not explicitly approved
- screenshots containing private dashboards, chats, accounts, or credentials
- business pricing, commercial terms, unreleased plans, or customer-specific
  strategy

## Required Placeholders

Use stable placeholders so readers can still understand the flow.

| Sensitive item | Placeholder |
| --- | --- |
| Owner name | `<OWNER>` |
| Executor name | `<EXECUTOR>` |
| Reviewer name | `<REVIEWER>` |
| project name | `<PROJECT>` |
| repo URL | `<REPO_URL>` |
| local path | `<LOCAL_PATH>` |
| production URL | `<PRODUCTION_URL>` |
| customer | `<CUSTOMER>` |
| token or key | `<SECRET>` |
| email | `<EMAIL>` |
| phone | `<PHONE>` |
| screenshot | `<REDACTED_SCREENSHOT_SUMMARY>` |

## Minimum Redaction Checklist

Before a case is committed:

- [ ] No absolute local path remains unless it is an intentional generic
      placeholder.
- [ ] No private repo URL remains.
- [ ] No credential, token, cookie, API key, webhook, session ID, or auth header
      remains.
- [ ] Screenshots are either omitted, cropped, blurred, or replaced by a text
      summary.
- [ ] Customer and commercial information is generalized.
- [ ] The reusable lesson is still understandable after redaction.
- [ ] Reviewer has recorded the redaction check in the target project's evidence
      ledger or review report.

## Mandatory Reviewer Redaction Approval

No case study or anti-pattern may be committed, published, shared with another
team, or used as a training/reference artifact until the Reviewer explicitly
approves redaction.

Reviewer approval must be recorded in the case file and in the source project's
review or evidence ledger.

Required approval fields:

```text
Redaction reviewed by:
Redaction review date:
Redaction result: approved / needs changes
Redaction evidence path:
Remaining disclosure risk:
```

If the Reviewer cannot inspect the source material, the case must remain
`Redaction Status: pending` and must not leave the source project.

## Reviewer Redaction Checks

Reviewer must check:

- all conversation excerpts
- all evidence excerpts
- all screenshots and image references
- all repository links and issue/PR links
- all local paths and machine/user identifiers
- all customer, product, commercial, and roadmap details
- all secrets, credentials, tokens, cookies, webhook URLs, auth headers, and
  session identifiers
- all public URLs that could reveal private work

Reviewer must reject the case when any sensitive material remains or when the
redaction cannot be verified from the submitted evidence.

## Conversation Excerpts

When exporting conversations:

1. Keep only the segments needed to explain the decision, mistake, correction,
   or reviewer judgment.
2. Replace long chat logs with a short timeline.
3. Preserve exact phrases only when they are useful as ACS protocol examples.
4. Summarize private implementation details rather than copying them.
5. Record the source project and phase using generic labels if the project is
   private.

## Evidence Excerpts

When exporting evidence:

- Prefer command names and result summaries over full logs.
- Include failed/passed counts when useful.
- Do not include raw environment variables.
- Do not include local machine paths.
- Do not include full screenshots unless explicitly approved and redacted.

## Reviewer Responsibility

The Reviewer must reject a case-study or anti-pattern submission when redaction
is incomplete, even if the technical lesson is valuable.

Redaction approval is a blocking ACS gate, not a suggestion.
