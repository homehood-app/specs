---
status: draft
updated: 2026-10-06
superseded-by:
---

# Start a task

As the executor of a task, I want to say I have begun so that the household knows it is being handled.

**Actors:** [[users#member]], [[users#organizer]], [[users#owner]], [[users#minor]]

## Pre-conditions

- The task exists and is in state `Open`
- The actor is its executor

## Main flow

1. The executor starts the task.
2. The system sets the task to `Started`.
3. The requester sees that it has begun.

## Alternative flows

None.

## Exception flows

### The actor is not the executor

1. The system refuses and says only the executor starts their task.
2. Nothing changes.

### The task is not `Open`

1. The system refuses and says the task is already started, closed or archived.
2. Nothing changes.

## Post-conditions

- The task is in state `Started`
- The task can now be archived, and can no longer be deleted by its requester

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every task in the household, and which are started | Start a task only when they are its executor |
| Organizer | Every task in the household, and which are started | Start a task only when they are its executor |
| Member | The tasks where they are the requester or the executor | Start a task they are the executor of |
| Minor | The tasks where they are the requester or the executor | Start a task they are the executor of |

## Applied business rules

- [[rules#the-executor-works-the-task]] — nobody starts another member's work
- [[rules#a-task-moves-in-one-direction]] — `Started` is the only state a task can be closed or archived from
- [[rules#who-can-end-a-task]] — starting is what moves a task from "deletable by its requester" to "archivable"
