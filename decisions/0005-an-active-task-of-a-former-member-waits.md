---
decision: 0005
date: 2026-10-07
status: accepted
supersedes:
superseded-by:
---

# 0005 — An active task of a former member waits for organizer authority

## Question

A member leaves a household, by their own choice or because they were removed. They were the requester or the executor of tasks. What happens to those tasks?

## Options

### A — Each task falls back automatically

A task the leaver was executing goes to its requester as the new executor. A task they requested goes to the owner as the new requester. A task where they were both goes to the owner as both.

- **Good:** No queue, no new state, no screen. The household never has to think about it.
- **Cost:** Somebody acquires work without being asked, which is the one thing [[0002-any-member-can-give-work-to-another]] made a deliberate social act. The requester may also be the person least able to do it. Worse, the rule it rests on — that no task may name somebody who is not a member — forces a closed or archived task of a former member to be rewritten or deleted, which destroys the record.

### B — The task keeps the former member, and waits for organizer authority

The task is **unresolved**. A member with organizer authority reassigns it, archives it, or deletes it — one at a time, or all at once.

- **Good:** Nothing is handed to anybody without a decision. Nothing is lost. The history stays whole, because a task naming a former member is normal rather than an error. Whoever removes a member can resolve the tasks in the same step.
- **Cost:** A state the household has to clear. An unresolved task can sit there.

### C — The departing member chooses who takes each task

- **Good:** The tasks are resolved at once, by the person who knows them best.
- **Cost:** The departing member is the one person with no stake in who picks up the slack, and they cannot know who is free. A member leaving in a hurry or on bad terms makes bad choices or none.

## Decision

Option B.

- A task keeps its requester and its executor after one of them leaves. So does a comment keep its author.
- A `Closed` or `Archived` task with a former member on it is finished. There is nothing to resolve.
- An `Open` or `Started` task with a former member on it is **unresolved** and waits.
- A member with organizer authority resolves it: give it to a member, archive it, or delete it. Resolving all at once archives every `Started` task and deletes every `Open` one.
- A member who leaves does not resolve their own tasks. A member with organizer authority who removes somebody may resolve them in the same step, or leave them unresolved.

## Reason

The argument that settled it is about history, not about work. A closed task that a former member executed is a record of something that happened in this home. So is every comment they wrote. If the model insists that no task may name a person who is not a member, then every departure rewrites the past — tasks would have to be reattributed to somebody who did not do them, or deleted. Neither is acceptable in a product whose point is knowing who did what.

Once a task is allowed to name a former member, an active task naming one stops being an anomaly to prevent and becomes a state to clear. That is what `unresolved` is.

Option A was rejected for a second reason as well: it hands work to somebody without asking. Asking a member to do something is a deliberate act in this product, and a fallback that quietly makes the requester the executor goes around it.

The queue always has somebody to work it, because **organizer authority** includes the owner, and a household always has exactly one owner. A household with no organizers is not a household with nobody to resolve.

## Affects

- [[domain]] — the **former member** concept
- [[modules/household/rules#a-former-member-stays-on-what-they-left-behind]]
- [[modules/household/rules#an-active-task-of-a-former-member-waits-for-organizer-authority]]
- [[modules/tasks/rules#an-unresolved-task-is-a-task-with-a-former-member-on-it]]
- [[modules/tasks/use-cases/08-resolve-a-former-members-tasks]]
- [[modules/household/use-cases/08-remove-a-member]] and [[modules/household/use-cases/09-leave-a-household]]

## When to revisit

If unresolved tasks pile up in real households, the answer is a reminder rather than an automatic fallback — the decision not to hand work over without asking is the part worth keeping.
