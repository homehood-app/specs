---
decision: 0012
date: 2026-10-07
status: accepted
supersedes:
superseded-by:
---

# 0012 — A routine for another member needs organizer authority

## Question

[[0002-any-member-can-give-work-to-another]] says any member can ask any member for work, because asking is not an act of authority. A routine is asking, repeated, with no end date. Does the same openness apply to it?

## Options

### A — Any member, for any member

The same rule as a single task. A minor can set a daily routine for a parent, exactly as they can ask a parent for one task today.

- **Good:** No exception to learn and no second rule. [[0002-any-member-can-give-work-to-another]] holds everywhere, and nobody has to work out why asking once is allowed and asking forever is not.
- **Cost:** A routine binds somebody's future with no end. A member can give another member standing work the other never agreed to, and the other cannot change it, pause it or end it — they can only do each occurrence or let it be missed. The answer to "why is this on my list every day?" becomes "because somebody put it there and only an organizer can take it off".

### B — A member sets a routine for themselves; naming another member needs organizer authority

Any member, a minor included, can set a routine for themselves. Only the owner and an organizer can set one that names somebody else, or a rotation.

- **Good:** The weight matches the act. A standing claim on somebody's weeks is the household's plan, and the household's plan belongs to whoever holds the household together. Every member keeps the useful half: their own recurring work, with no permission needed.
- **Cost:** It is an exception to [[0002-any-member-can-give-work-to-another]], and exceptions have to be remembered. A member who wants a flatmate to take the bins every week has to ask an organizer instead of just setting it.

### C — Owner and organizer only, for everybody

No member sets a routine at all.

- **Good:** One rule, complete control of the household's plan.
- **Cost:** A member cannot set up their own recurring work, which is the least objectionable thing in the module. It makes the product worse for the person it costs nothing to trust.

## Decision

Option B.

- Any member can create a routine with themselves as its only executor. A minor can too
- Only the owner and an organizer can create a routine that names another member as its executor
- Only the owner and an organizer can create or change a rotation, because a rotation names other members
- A member can change, pause, end or delete a routine they created for themselves
- A member who is the executor of a routine somebody else created cannot change it, pause it or end it. They do each occurrence

## Reason

The difference between a task and a routine is that a task ends. [[0002-any-member-can-give-work-to-another]] rests on asking being a social act — you ask, the other does it or does not, and it is over. A routine is not that act. It is a standing instruction with no end date that keeps producing work until somebody with authority stops it, and the member it is aimed at cannot stop it themselves. Giving every member that instrument is not the same as letting every member ask.

This is a boundary, not a reversal. [[0002-any-member-can-give-work-to-another]] stays accepted and unchanged: any member can still ask any member for a task, and a minor can still ask a parent. What this record says is that the openness does not extend to a new instrument that behaves differently. [[modules/tasks/rules#any-member-can-request-work-from-any-member]] is untouched.

Option A was argued seriously, on consistency: the team chose openness twice, in 0002 and again in the reasoning of [[0005-an-active-task-of-a-former-member-waits]], and an exception weakens both. It was rejected because consistency is the weaker claim here. The two acts are not alike, so treating them alike is not consistency — it is a resemblance in the wording.

The rule that the executor of somebody else's routine cannot change it is the part to watch. It is deliberate: a member who could pause a routine set for them could opt out of the household's plan, and the plan would mean nothing. The member's recourse is to ask, which is what the household did before the product existed.

## Affects

- [[modules/routine/rules#a-member-sets-a-routine-for-themselves-naming-another-member-needs-authority]]
- [[modules/routine/use-cases/01-create-a-routine-for-myself]] and [[modules/routine/use-cases/02-create-a-routine-for-another-member]] — two use cases because the authority differs
- [[modules/routine/use-cases/03-set-a-rotation-on-a-routine]] — a rotation always needs authority
- [[modules/routine/use-cases/06-edit-a-routine]], [[modules/routine/use-cases/07-pause-and-resume-a-routine]], [[modules/routine/use-cases/08-end-a-routine]] and [[modules/routine/use-cases/09-delete-a-routine]] — the same authority governs each
- [[0002-any-member-can-give-work-to-another]] — unchanged, and bounded to a single task by this record
- [[users]] — no change. What a role may do in one area of the product belongs to the module

## When to revisit

If flat shares find it absurd that an adult cannot set a weekly bins rotation without being an organizer, the answer is probably that a flat share makes everybody an organizer, not that this rule is wrong. Revisit if that turns out not to work in practice.

Revisit also if members start asking to decline a routine set for them. Declining is not in the product today, and it is the honest form of the cost this decision accepts.
