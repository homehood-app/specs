---
decision: 0006
date: 2026-10-07
status: accepted
supersedes:
superseded-by:
---

# 0006 — A minor is reduced on the household, not on the work

## Question

[[0004-four-roles-owner-organizer-member-minor]] made minor the fourth role and said it "does what a member does and sees less of it". It did not say what *less* is, and `users.md` carried the gap as **Not yet decided**. A minor had exactly a member's authority, so the role narrowed nothing. Which part of the product is reduced for a minor: the work, the task, or the household?

## Options

### A — Reduce the work

A minor sees fewer of their own tasks, or cannot end one: no deleting a request, no archiving a started task.

- **Good:** Work cannot leave the board without an adult. When points arrive, a child cannot make a task disappear instead of doing it or failing it.
- **Cost:** Breaks what the role is for. A child who changes their mind about a request has to ask an adult to undo a task the child created a minute ago. Hiding a task from the person who has to do it is incoherent, and a child who cannot see their own finished work has no record of what they did.

### B — Reduce the household

A minor keeps a member's authority over the work, in full. What is removed is the household's machinery: who holds authority, and the fact that a task is waiting on an adult decision.

- **Good:** Nothing a child needs is taken away. A minor still sees who asked, what was said, and everything they have done. What goes is the part a child has no use for and no power over — which member is the owner, which members are organizers, and that a task of theirs is unresolved.
- **Cost:** It is a thin reduction. On most use cases the minor row is identical to the member row, so the role carries little behavior of its own and reads at first as a label.

### C — Reduce the task

Keep a member's authority, and strip the task down: no requester, no comments. A list of things to do.

- **Good:** The plainest possible view. One screen, one list, no names.
- **Cost:** Takes away the two things that make a task answerable. A task with no requester comes from nobody, so the child cannot go back to the person who asked. Comments are how a parent says *how*, so removing them leaves instructions with nowhere to live.

## Decision

Option B. A minor has a plain member's authority over the work, with nothing removed, and sees nothing of how the household is run.

Hidden from a minor:

- Which member is the owner, and which members are organizers. A minor sees every member by name, and no role but their own
- That a task of theirs is **unresolved** — waiting on organizer authority because the person on the other side of it has left

Not hidden from a minor:

- Who requested the task, and who will do it
- The comments on the task
- Their own closed and archived tasks

A minor's one narrowed act is on their membership, not on the work: a minor cannot leave a household on their own. A member with organizer authority takes them out.

Everything else is a plain member's: a minor asks any member for work, edits their tasks, starts them, closes them, comments on them, deletes a request nobody started, and archives a started task of theirs.

## Reason

The reduction had to come out of something a child has no use for, and all three candidates were tested against that.

The work failed the test. A child's own tasks are the reason a child is in the product at all, and the acts that end them are the ones the child has the most legitimate claim to: a request they made, and work they began. Making those adult-only turns a one-second correction into a negotiation, every time.

The task failed it harder. The requester and the comments are not decoration — they are who asked and what they want. A task without them is an order from nobody.

The household passed. A child does not administer the home. Who is the owner, who was promoted, which invitation is pending, which task is stuck waiting for a parent to decide — none of it is actionable by a minor, and all of it is the household's business rather than the child's. Removing it is honest reduction: the information is gone, not just moved off a screen.

That thinness is the cost and it is accepted. The role is worth having with two rules in it, because the ladder is already right — a minor organizer and a minor owner do not exist — and because this record is the place the next difference gets added. "Maybe in the future we add other differences" is exactly what the role is holding open.

Archiving is the one place where the chosen answer runs against the advice given: a minor can archive a started task of their own. The risk is named under **When to revisit**.

## Affects

- [[domain]] — Minor says what is reduced, instead of saying it is unspecified
- [[users]] — the Minor member persona, and the **Not yet decided** block is gone
- [[modules/household/rules#a-minor-does-not-see-who-runs-the-household]] — the information that is hidden
- [[modules/household/rules#a-minor-cannot-take-themselves-out-of-a-household]] — the one narrowed act
- [[modules/household/use-cases/09-leave-a-household]] — a minor is refused, and pointed at removal
- [[modules/household/use-cases/08-remove-a-member]] — the only way a minor leaves
- [[modules/household/use-cases/07-transfer-ownership]] — a minor sees nothing of it
- [[modules/household/use-cases/06-change-a-members-role]] — a minor sees their own role and no other
- [[modules/tasks/rules#a-minor-sees-their-own-work-in-full]] — the work is not reduced
- [[modules/tasks/use-cases/08-resolve-a-former-members-tasks]] — a minor is not told their task waits

## When to revisit

When points or any other reward land on a closed task. A minor can archive a started task of their own, and archiving is how a started task ends without being finished. If that becomes a way to drop work and keep a score clean, archiving by a minor should move to organizer authority — and that is a new record, not an edit to this one.

Also when the product gives a minor something a member does not have, rather than less. This record only says what is taken away.
