---
decision: 0013
date: 2026-10-07
status: accepted
supersedes:
superseded-by:
---

# 0013 — A routine with a former member on it pauses

## Question

A member leaves a household and a routine names them — as its executor, as its requester, or as a place in its rotation. [[0005-an-active-task-of-a-former-member-waits]] answered this for a task that already exists. A routine is different: it points forwards and keeps making new work. What happens to it?

## Options

### A — The routine pauses and waits for organizer authority

It makes no further occurrence. A member with organizer authority names a new executor or fixes the rotation and makes it active again, or ends it.

- **Good:** The same shape as [[0005-an-active-task-of-a-former-member-waits]]: nothing is handed to anybody without a decision, and nothing is lost. The record of the turns the former member did stays whole. A routine that nobody resolves simply stops asking, which is quiet and harmless.
- **Cost:** A part of the household's routine stops working until somebody notices. The dishes are not asked for, and the household may not realise why.

### B — The routine keeps going, and each occurrence is unresolved

It carries on making occurrences, each one naming a former member, each one unresolved under [[0005-an-active-task-of-a-former-member-waits]].

- **Good:** Nothing stops. The work keeps being asked for, so the household cannot quietly forget the routine exists.
- **Cost:** The queue of unresolved tasks refills itself every single day. [[0005-an-active-task-of-a-former-member-waits]] accepted a queue the household has to clear, on the understanding that it is finite. A routine makes it infinite, and resolving it one occurrence at a time can never finish.

### C — The routine is deleted

The member left, so their routines go with them.

- **Good:** No queue and nothing to decide.
- **Cost:** The household loses a part of its routine because one person left, along with the record of every turn that person did. The dishes were a household routine before the leaver and will be one after, and deleting it destroys history for no gain — the thing [[0005-an-active-task-of-a-former-member-waits]] refused to do.

## Decision

Option A.

- A member is **on** a routine when they are its requester, its executor, or in its rotation
- When a member on a routine stops being a member, the routine pauses at once and makes no further occurrence
- It pauses even when the rotation still holds enough members to carry on
- A member with organizer authority resolves it: name a new executor or fix the rotation and make it active again, or end it
- Occurrences the routine already made keep the former member and follow [[modules/tasks/rules#an-unresolved-task-is-a-task-with-a-former-member-on-it]]
- The routine keeps the former member on every occurrence they did

## Reason

[[0005-an-active-task-of-a-former-member-waits]] settled two things, and both apply unchanged. History is not rewritten, so the occurrences the leaver did keep their name. And work is not handed to anybody without a decision, so no member inherits a daily commitment because somebody else left.

What is new is that a routine produces work. Option B is the only option that respects 0005's letter and breaks its logic: 0005 accepted a queue because a queue is finite and can be cleared, and a routine that keeps generating turns it into a tap that cannot be turned off by clearing. Pausing turns the tap off and leaves the decision where 0005 put it.

A routine pauses even when the rotation could carry on without the leaver, and that is deliberate. Dropping a member out of a rotation silently changes how often everybody else is asked — a rotation of three becoming two means each remaining member does the work half the time instead of a third. That is a change to the household's plan, and the household should make it rather than have it happen to them.

Option C was rejected on the same ground 0005 rejected rewriting a task: the routine is the household's, not the leaver's.

The cost is accepted: a paused routine stops asking, and nobody is told. Reminders are out of scope for this module, so today the household finds out by looking. That is the weakest part of this decision.

## Affects

- [[modules/routine/rules#a-routine-with-a-former-member-on-it-pauses]]
- [[modules/routine/use-cases/10-resolve-a-routine-of-a-former-member]]
- [[modules/routine/use-cases/07-pause-and-resume-a-routine]] — the one pause nobody chose
- [[modules/routine/domain]] — **a member on a routine**
- [[0005-an-active-task-of-a-former-member-waits]] — this record applies its decision to a thing that points forwards
- [[modules/household/use-cases/08-remove-a-member]] and [[modules/household/use-cases/09-leave-a-household]] — the departure that triggers it

## When to revisit

When notifications are specified. The cost of this decision is that a paused routine is silent, and a notification is the answer to that — not an automatic fallback, for the reason [[0005-an-active-task-of-a-former-member-waits]] gives.
