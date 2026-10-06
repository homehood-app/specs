---
decision: 0002
date: 2026-10-06
status: accepted
supersedes:
superseded-by:
---

# 0002 — Any member can give work to another member

## Question

Asking for a task is an act on another person's time. Can every member do it, or only a member with authority?

## Options

### A — Only a member with authority can request work from somebody else

- **Good:** Matches a household where one person runs the schedule. Nobody can be handed work by a peer.
- **Cost:** Wrong for a flat share of equals, where anybody may need to ask anybody. Makes a request as small as "please buy milk" wait on someone with a title.

### B — Any member can request work from any member

- **Good:** Matches how a shared home actually talks. A request from one member to another is normal, and routing it through someone with authority adds nothing.
- **Cost:** A member can be asked by anybody. Nothing stops a member handing out work they should be doing themselves.

### C — Any member can request work, and the other member must accept it

- **Good:** Nobody is the executor of work they did not agree to.
- **Cost:** A second state and a second step on the most common action in the product. Most households do not need a negotiation protocol to decide who takes the bins out.

## Decision

Option B. Any member can create a task with any member of the same household as its executor.

## Reason

A shared home is a place where people ask each other for things. Reserving that to a role describes a household that does not exist, and turns whoever holds the role into a dispatcher for every small request.

We rejected C because the cost lands on the most frequent action in the product. An acceptance step is worth building when the social cost of unwanted work is high; inside one home, the cheaper correction is to talk, or to edit the task.

The protection against abuse is social rather than technical, and that is a deliberate choice. If it turns out not to hold, C is the upgrade path and it does not require this decision to be reversed — only extended.

## Affects

- [[modules/tasks/rules#any-member-can-request-work-from-any-member]]
- [[modules/tasks/use-cases/01-create-a-task]]

## When to revisit

If households report members being handed work they did not want, option C is the next step.
