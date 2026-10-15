---
name: project-journal
description: >-
  Keep a living project journal (JOURNAL.md, STATUS.md, QUESTIONS.md, CHANGELOG.md)
  up to date WITHOUT being asked. Use it whenever you start working on a project
  that has a journal, right after any important decision (price, name, stack,
  design, scope, something killed or postponed, a corrected fact, an approved
  file), at the end of a stage or session, and when the user says "update the
  journal", "log this" or "don't forget this". Also use it to create a journal
  for any project that will last more than one session.
---

# Project journal

A journal exists so that neither the user nor Claude forgets what was decided, why, and what is left. The most common failure is not a bad journal, it is a journal nobody updated after the decision. This skill fixes that.

Reply to the user in their language. Write the journal in the language the project already uses.

## The main rule

**A decision that is not in the journal has not been made.** Update it in the same turn the decision closes, not at the end of the session and not when the user asks.

## When to update (triggers)

Update without asking when any of these happen.

1. The user approves or closes something ("ok", "go ahead", "keep it like that", "approved", "done").
2. A business fact changes. Price, discount, product name, domain, deadline.
3. Stack, folder structure, repository, deploy or tooling changes.
4. A design choice changes. Font, palette, layout, tone, visual canon.
5. Something is killed or postponed. Log it with its reason, so nobody proposes it again.
6. An error or a false fact is corrected (in code, copy, docs).
7. A file is delivered or approved (version, path, backup).
8. A blocking open question appears, or a to-do with an owner.
9. The project drifts from its original premise. Name the drift explicitly.
10. A stage or the session ends.

If five turns in a row changed something and the journal was not touched, stop and update it before continuing.

## When starting work on a project

1. Find the journal (`JOURNAL.md`, `BITACORA.md`, `STATUS.md`, `QUESTIONS.md`, `CHANGELOG.md`, or whatever the project uses).
2. Read the **CURRENT STATE** block first. It overrides everything below it.
3. Read the latest log entries and the open to-dos.
4. If the current state has an old date or contradicts the log, say so in one line before working.
5. If there is no journal and the project will last more than one session, propose creating one with the template below.

## Formats and when to use each

**1. Main journal (whole project).** Blocks in this order.
- `## CURRENT STATE · YYYY-MM-DD · overrides everything below` with a short table (what it is, where it lives, phase, open front, pending decision).
- Alerts for what must be verified today and for what is now false (stale code comments, outdated docs).
- Fixed sections such as stack, visual system, numbered active decisions, roadmap, **Killed / postponed, with reason**, and immediate to-dos with an owner.
- `## Log (append-only)` with `### YYYY-MM-DD, topic` entries and bullets starting with Decided, Killed, Postponed, Fixed, Verified, Pending.

**2. Product diary (append-only, newest on top).** Each entry states what was decided (with the user's exact words if any), where every number comes from, the **verification that was run**, and what is left. Zero invented numbers. Anything unknown is marked `[PENDING]`.

**3. STATUS per iteration.** `## YYYY-MM-DD, vN state`, what was produced (paths), decisions taken in this iteration, verification run, what is left.

**4. QUESTIONS.** `## YYYY-MM-DD HH:MM, QN` with Blocking yes or no, Context (what was verified, with file and line) and Question. When answered, add the answer below it, never delete.

**5. CHANGELOG (software).** Keep a Changelog style. `## vX.Y.Z, YYYY-MM-DD, summary` with Added, Changed, Fixed and Removed sections.

**6. Content or narrative journal.** Sessions by date, in the user's own words, with privacy marks per item. Public (fine to publish), Ask first (involves third parties or exposes the user), Private (stays private). Nothing is published without explicit approval.

**7. Drift.** When the project is no longer what its premise said, add a `Drift, named` section, keep the original mandate as history, and name the open decision it leaves.

## Writing rules

- **Append-only.** Never delete or rewrite old entries, and never rewrite what the user wrote. If something is superseded, mark it as superseded and point to the new entry.
- **Always refresh the CURRENT STATE block** and its date when anything it summarizes changes. A stale state on top is worse than none.
- Absolute dates (`2026-10-14`), never "yesterday" or "next week".
- Every decision carries its **why** in one line. Every killed item carries its reason.
- Numbers, prices and claims only when verified. Everything else is `[PENDING]` or "unconfirmed".
- Exact file paths and version names.
- No secrets, no credentials, no sensitive third-party data.

## Backups and git

- After an approved stage, make a versioned ZIP of that stage in the project's backup folder and mention it in the entry.
- If the journal lives in a repository, tell the user which files changed and suggest a short commit message, unless the user asked Claude to commit.

## How to report it

At the end of the reply where you updated, add one line. For example "Journal updated in `JOURNAL.md`, current state and log 2026-10-14 (base price set to 40)". If you could not access the file, say so and leave the entry text ready to paste.

## Template for a new journal

```
# JOURNAL · <project>

*Opened YYYY-MM-DD. Why it exists in one sentence.*

---

## CURRENT STATE · YYYY-MM-DD · overrides everything below

| | |
|---|---|
| what it is | |
| phase | |
| lives at | |
| open front | |
| pending decision | |

---

## Active decisions
1.

## Killed / postponed (with reason)
-

## To-do (with owner)
- User,
- Claude,

---

## Log (append-only)

### YYYY-MM-DD, topic
- Decided,
- Verified,
- Pending,
```

## Checklist before finishing each reply

1. Did a decision, fact, file or to-do close in this turn? If yes, is it in the journal?
2. Is CURRENT STATE still true, and dated today if it changed?
3. Do killed items have a reason, and do unverified items say `[PENDING]`?
4. Is there a backup of the stage if something was approved?
5. Did I say in one line which file I updated?
