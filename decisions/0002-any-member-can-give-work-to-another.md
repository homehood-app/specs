---
decision: 0002
date: 2026-10-06
status: accepted
supersedes:
superseded-by:
---

# 0002 — Any member can give work to another member

## Question

Creating a task for somebody else is an act on another person's time. Is it reserved to organizers, or open to every member?

## Options

### A — Only an organizer can create a task for another member

- **Good:** Matches a household where one person runs the schedule. Gives the organizer role a clear job beyond membership. Nobody can be handed work by a peer.
- **Cost:** Wrong for a flat share of equals, where anybody may need to ask anybody. Makes the organizer a bottleneck for a request as small as "please buy milk".

### B — Any member can create a task for any member

- **Good:** Matches how a shared home actually talks. A request from one member to another is normal, and routing it through an organizer adds nothing. The organizer keeps the authority that matters — who belongs to the household, and what gets removed from it.
- **Cost:** A member can be given work by anybody. There is no protection against a member who hands out tasks they should be doing themselves.

### C — Any member can offer a task, and the other member must accept it

- **Good:** Nobody owns work they did not agree to.
- **Cost:** A second state and a second step on the most common action in the product. Most households do not need a negotiation protocol to decide who takes the bins out.

## Decision

Option B. Any member can create a task for any other member of the same household. The organizer's authority is membership and deletion: invite a person, remove a member, delete a task.

## Reason

A shared home is a place where people ask each other for things. Making that an organizer's privilege describes a household that does not exist, and turns the organizer into a dispatcher for every small request.

We rejected C because the cost lands on the most frequent action in the product. An acceptance step is worth building when the social cost of unwanted work is high; inside one home, the cheaper correction is to talk, or to edit the task.

The protection against abuse is social rather than technical, and that is a deliberate choice. If it turns out not to hold, C is the upgrade path and it does not require this decision to be reversed — only extended.

## Affects

- [[modules/tasks/rules#any-member-can-give-work-to-any-member]]
- [[modules/tasks/use-cases/create-a-task]]
- [[users]] — a member's authority now includes giving work to another member

## When to revisit

If households report members being handed work they did not want, option C is the next step.
