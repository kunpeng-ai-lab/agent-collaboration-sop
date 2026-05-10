# ACS Public Screenshot Plan

Status: public-safe screenshot brief
Redaction status: sanitized

Use screenshots to show ACS as a real engineering workflow, not a concept-only
method. Every screenshot must avoid local paths, private repositories, customer
names, credentials, raw chats, and unreleased business details.

## Recommended Screenshot Set

| Shot | Source | What It Should Prove | Public Caption | Redaction Notes |
| --- | --- | --- | --- | --- |
| README overview | `README.md` | ACS has a clear role model and workflow | "ACS defines Owner / Executor / Reviewer collaboration as an auditable workflow." | Crop to headings and public repo content only. |
| Case studies index | `case-studies/README.md` | ACS stores reusable collaboration lessons | "Case studies turn phase closures into reusable engineering memory." | Do not show private source project names. |
| Anti-pattern index | `anti-patterns/README.md` | ACS keeps failure modes as reusable prevention checklists | "Anti-patterns are teaching assets, not blame records." | Show sanitized anti-pattern names only. |
| Evidence ledger template | `templates/evidence-ledger.md` | Evidence is file-based and reviewable | "Evidence ledgers preserve commands, screenshots, decisions, and remaining risks." | Template only; no real project data. |
| Reviewer report template | `templates/reviewer-report.md` | Reviewer checks more than tests | "Reviewer reports cover command, evidence, product, architecture, security, and redaction gates." | Template only. |
| Executor handoff template | `templates/executor-handoff.md` | Executor handoff is structured | "Executor handoffs include ACS sync, behavior scenarios, constraints, changed files, and verification." | Template only. |
| Redaction rules | `docs/case-study-redaction.md` | Public cases are sanitized before reuse | "Public ACS cases keep the lesson and remove private details." | Template/rules only. |
| PR or issue page | Public repo PR/issue when available | ACS can govern public collaboration, not just local work | "ACS cases can link decisions, review gates, and merge readiness." | Use only public repository pages; blur usernames if needed. |

## Generated Public-Safe Screenshot Assets

The `screenshots/` directory contains generated screenshot-style images based on
sanitized ACS excerpts. They are safe for article drafts and presentations, but
should be replaced by real public repo screenshots when the final page design
needs exact UI.

Planned/generated files:

- `acs-readme-overview.png`
- `acs-case-studies-index.png`
- `acs-anti-patterns-index.png`
- `acs-evidence-ledger-template.png`
- `acs-reviewer-report-template.png`
- `acs-executor-handoff-template.png`
- `acs-redaction-rules.png`

## Screenshot Redaction Checklist

- [ ] No local absolute path is visible.
- [ ] No private repo URL is visible.
- [ ] No token, cookie, API key, session ID, or webhook URL is visible.
- [ ] No customer name or private project name is visible.
- [ ] No unreleased commercial or roadmap information is visible.
- [ ] No raw private chat transcript is visible.
- [ ] Cropped region still teaches the ACS point.
- [ ] Reviewer redaction approval is recorded before publishing.

