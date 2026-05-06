# Reviewer Product Validation

Reviewer approval requires product validation when the task affects any user
experience, UI, workflow, dashboard, page, report, public content, or customer
visible artifact.

Automated tests are not enough for product-facing work.

## When This Applies

Use this document for:

- frontend pages and prototypes
- dashboards and workbenches
- customer or operator workflows
- reports, exports, and public documents
- content pages, landing pages, docs, and blog pages
- CLI or agent workflows that users operate directly
- any task where the Owner cares about the real user outcome

## Required Product Validation Questions

Reviewer must answer:

1. What user role is this for?
2. What job is the user trying to complete?
3. What is the intended happy path?
4. What failure or empty states matter?
5. Does the implementation match the approved product direction?
6. Does the UI or workflow expose internal engineering language to users?
7. Does the flow create new confusion, dead ends, or unsupported actions?
8. Does it preserve the project's short-term and long-term goals?

## Required Page-Level Validation

For UI or prototype work, Reviewer must verify at least:

- the relevant page or screen opens
- the main workflow can be followed manually
- key controls are visible and usable
- important copy is user-facing, not internal-agent wording
- layout does not obviously break at the target viewport
- the changed area does not hide or damage adjacent workflows
- screenshots or equivalent visual evidence are stored when practical

For local prototypes, browser checks may use localhost, static HTML, or the
project's documented preview command. If browser execution is impossible, the
Reviewer must explain why and perform a source-level fallback review.

## Conversation Summary vs Detailed Report

Reviewer-to-Owner and Reviewer-to-Executor messages should include only a short
summary, not the full product validation report.

The message must include:

- product validation result: pass / needs changes
- pages or workflows checked
- key risk or finding summary
- detailed report path in the project repository

Example:

```text
Product validation: needs changes.
Checked: operator daily workbench and report preview.
Issue summary: the primary workflow can be opened, but the correction action
uses internal implementation wording and lacks an empty state.
Detailed report: reviews/<phase>/product-validation.md
```

## Report File Requirement

The detailed report belongs in the target project, not only in chat.

Recommended path:

```text
reviews/<phase>/product-validation.md
```

The report should include:

- ACS version
- role and workflow checked
- browser or preview method
- viewport or environment
- screenshots or screenshot paths when practical
- findings
- non-blocking observations
- remaining risks

## Redline

For product-facing work, a review that only says "tests pass" is incomplete.

