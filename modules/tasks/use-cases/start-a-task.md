---
status: draft
updated: 2026-10-06
superseded-by:
---

# Start a task

As the owner of a task, I want to say I have begun so that the household knows it is being handled.

**Actors:** [[users#member]], [[users#organizer]], [[users#minor-member]]

## Pre-conditions

- The task exists and is in state `Open`
- The actor owns it

## Main flow

1. The owner starts the task.
2. The system sets the task to `Started`.

## Alternative flows

None.

## Exception flows

### The actor does not own the task

1. The system refuses and says only the owner starts their task.
2. Nothing changes.

### The task is not `Open`

1. The system refuses and says the task is already started, closed or archived.
2. Nothing changes.

## Post-conditions

- The task is in state `Started`

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Organizer | Every task in the household, and which are started | Start a task only if they own it |
| Member | The tasks they own and the tasks they created | Start a task they own |
| Minor member | The tasks they own and the tasks they created | Start a task they own |

## Applied business rules

- [[rules#the-owner-works-the-task]] — only the owner starts it
