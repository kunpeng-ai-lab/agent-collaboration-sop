# Evidence Patterns

Redaction Status: reviewer-approved

## Command Evidence

Good evidence:

- default test command output
- encoding-check script output
- source scan showing target IDs appear exactly once
- source scan showing expected script imports

Weak evidence:

- "tests pass" without command and count
- "fixed" without diff or file reference
- screenshots without role/page context

## Product Evidence

For page/prototype work, include:

- page name
- role used for validation
- happy path checked
- empty state checked
- browser console status
- screenshot filename
- notes on adjacent pages

## Architecture Evidence

Include:

- new module list
- dependency direction
- no forbidden imports
- line-count guard
- script/module count
- scope and non-scope verification

## Redaction Evidence

For public ACS case reuse:

- use placeholders for paths, repos, project names, and actors
- omit raw screenshots unless cropped/blurred
- summarize commands instead of pasting full private logs
- do not include raw tokens or environment variables
