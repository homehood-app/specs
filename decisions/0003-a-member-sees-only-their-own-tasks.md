---
decision: 0003
date: 2026-10-06
status: accepted
supersedes:
superseded-by:
---

# 0003 — A member sees only their own tasks

## Question

Who can see which tasks? Does the household share one list, or does each member see only what concerns them?

## Options

### A — Every member sees every task in the household

- **Good:** One shared picture. Anybody can answer "who is doing this, and is it done?" without asking. Nobody has to chase a status.
- **Cost:** Everybody's work is everybody's business. A member cannot keep a task to themselves, and the list grows noisy as the household grows.

### B — A member sees only their own tasks; an organizer sees every task

- **Good:** Each member opens the product and sees exactly what is theirs, and nothing else. The organizer still has the full picture, which is where the overview is actually needed.
- **Cost:** The shared view is gone for everybody except the organizer. A member cannot see that somebody else has already taken care of something.

## Decision

Option B. A member sees the tasks they own and the tasks they created. An organizer sees every task in the household.

## Reason

The member's problem is "what do I have to do", not "what is everyone doing". A list that answers the first question in one screen is worth more to them than a household feed they have to filter.

The full picture matters to whoever is holding the household together, and that is the organizer. They keep it.

The creator keeps sight of a task they created for somebody else. Without that, [[0002-any-member-can-give-work-to-another]] would be hollow: you could hand out work and never learn whether it was done.

This narrows what [[overview]] promises. The value proposition was written as everybody reading the same answer; under this decision, everybody knows what is theirs and the organizer sees the whole household. `overview.md` was corrected in the same change that recorded this decision.

## Affects

- [[modules/tasks/rules#a-task-is-visible-to-its-owner-its-creator-and-every-organizer]]
- Every use case in [[modules/tasks/use-cases/index]] — the **By role** tables carry this rule
- [[overview]] — the core value proposition

## When to revisit

If members start asking who is doing the rest of the work, a shared household view is the answer, and this record should be superseded rather than edited.
