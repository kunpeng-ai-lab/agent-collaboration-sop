# Anti-Pattern: Handoff Says Fixed, Formal Doc Still Says Otherwise

Redaction Status: reviewer-approved

## Pattern

The Executor's handoff says a finding is fixed, but the formal planning document
still contains the stale command, stale scope, stale version, or stale
instruction.

## Why It Is Dangerous

Future work usually follows the document, not the chat summary. If the document
still contains the old instruction, the next implementation can repeat the exact
mistake that the review was supposed to prevent.

## Typical Signals

- Handoff version and document version do not match.
- A "removed" command is still in the file.
- A "changed" scope still appears in another section.
- A "safe" architecture rule is contradicted by a lower table.
- Evidence paths are updated in chat but not in the package.

## Reviewer Response

Block the handoff until:

- the formal document matches the chat summary
- stale instructions are removed
- version and message IDs are traceable
- the reviewer can search the document and find no conflicting instruction

## Prevention Checklist

- [ ] Search the file for old command names.
- [ ] Search the file for old version names.
- [ ] Search the file for old scope wording.
- [ ] Confirm Message ID and Responds To fields.
- [ ] Confirm the evidence paths are listed in the formal document.
- [ ] Run the default tests after the correction.
