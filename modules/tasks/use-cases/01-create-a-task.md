---
status: draft
updated: 2026-10-06
superseded-by:
---

# Create a task

As a member, I want to ask for a piece of work so that it has somebody attached to it.

**Actors:** [[users#member]], [[users#organizer]], [[users#owner]], [[users#minor-member]]

## Pre-conditions

- The actor is a member of the household

## Main flow

1. The member writes what the task is.
2. The member chooses the executor: themselves, or another member of the household.
3. The system creates the task in state `Open`, inside that household.
4. The system records the member as the requester, and the chosen member as the executor.

## Alternative flows

### No executor is chosen

1. The system makes the requester the executor as well.

### The executor is somebody else

1. The requester and the executor are two different members.
2. Both of them see the task from now on, and so do the owner and every organizer.

## Exception flows

### The chosen executor is not a member of the household

1. The system refuses and says the person is not in this household.
2. No task is created.

### The task has no description

1. The system refuses and asks what the task is.
2. No task is created.

## Post-conditions

- The task exists in state `Open`
- The task has exactly one requester and exactly one executor, both members of the household
- The requester, the executor, the owner and every organizer can see it

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every task in the household | Create a task with any member as the executor |
| Organizer | Every task in the household | Create a task with any member as the executor |
| Member | The tasks where they are the requester or the executor | Create a task with any member as the executor |
| Minor member | The tasks where they are the requester or the executor | Create a task with any member as the executor |

## Applied business rules

- [[rules#any-member-can-request-work-from-any-member]] — asking somebody else is not reserved to a role
- [[rules#every-task-has-a-requester-and-an-executor]] — one of each, fixed at creation
- [[rules#a-task-is-visible-to-its-requester-its-executor-the-owner-and-every-organizer]] — who can see it from now on
