# ACS Sync Rules

ACS changes over time. Agents must not rely on stale local rules.

## Sync Triggers

An agent must sync ACS in any of these cases:

1. **Daily scheduled sync**
   - If the runtime supports scheduled jobs, sync ACS every day at 06:00 local
     time.

2. **First task of the day**
   - If scheduled jobs are not available, sync ACS before the first project task,
     design task, coding task, test task, review task, handoff, or report of the
     day.

3. **Explicit Owner or Reviewer request**
   - If Owner or Reviewer says "同步 ACS", "更新 ACS", "按最新 ACS 执行", or an
     equivalent instruction, sync ACS immediately.

## Required Commands

Use the actual local ACS path for the current machine:

```powershell
cd <ACS 本地路径>
git pull origin main
git rev-parse --short HEAD
```

## Required Evidence

After syncing, the agent must report:

- ACS local path
- ACS current version from `git rev-parse --short HEAD`
- whether `git pull origin main` was executed
- sync failure reason if the sync failed

Do not claim ACS is synced without reporting the version.

## ACS Adoption Check

Syncing is not enough. The agent must also adopt the latest rules.

After sync, run `docs/acs-adoption-check.md` when:

- Owner or Reviewer explicitly requests latest ACS
- ACS version changed after `git pull`
- this is the first project task of the day
- a new redline, template, review gate, or case-study rule was added
- Reviewer doubts the agent is following the latest ACS behavior

Adoption evidence must include:

- files read after sync
- delta summary in the agent's own words
- behavior update
- memory/project-rule update confirmation
- limitations if long-term memory cannot be updated

ACS sync without adoption is incomplete when an Adoption Check is required.

## Message Requirements

Executor must include ACS sync evidence in the current `Message To Reviewer`,
handoff, blocked note, or review request.

Reviewer must check ACS sync evidence before accepting the handoff.

If ACS sync evidence is missing, Reviewer must ask Executor to correct the
handoff before substantive review.
