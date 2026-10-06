---
status: draft
updated: 2026-10-06
superseded-by:
---

# Create a task

As a member, I want to open a task so that a piece of the household's work has an owner.

**Actors:** [[users#member]], [[users#organizer]], [[users#minor-member]]

## Pre-conditions

- The actor is a member of the household

## Main flow

1. The member writes what the task is.
2. The member chooses who owns it: themselves, or another member of the household.
3. The system creates the task in state `Open`, inside that household, owned by the chosen member.

## Alternative flows

### No owner is chosen

1. The system owns the task to the member who created it.

### The task is for another member

1. The system records the creator separately from the owner.
2. Both of them can see the task from now on.

## Exception flows

### The chosen owner is not a member of the household

1. The system refuses and says the person is not in this household.
2. No task is created.

### The task has no description

1. The system refuses and asks what the task is.
2. No task is created.

## Post-conditions

- The task exists in state `Open`
- The task has exactly one owner, who is a member of the household
- The creator and the owner can both see it, and so can every organizer

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Organizer | Every task in the household | Create a task for themselves or for any member |
| Member | The tasks they own and the tasks they created | Create a task for themselves or for any member |
| Minor member | The tasks they own and the tasks they created | Create a task for themselves or for any member |

## Applied business rules

- [[rules#any-member-can-give-work-to-any-member]] — creating for somebody else is not reserved to organizers
- [[rules#a-task-has-exactly-one-owner]] — one owner, chosen at creation
- [[rules#a-task-is-visible-to-its-owner-its-creator-and-every-organizer]] — who can see it from now on
