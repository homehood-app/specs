---
status: draft
updated: 2026-10-07
superseded-by:
---

# Close a task

As the executor of a task, I want to say the work is finished so that nobody has to ask.

**Actors:** [[users#member]], [[users#organizer]], [[users#owner]], [[users#minor-member]]

## Pre-conditions

- The task exists and is in state `Started`
- The actor is its executor

## Main flow

1. The executor closes the task.
2. The system sets the task to `Closed`.
3. The requester, the owner and every organizer see that it is closed.

## Alternative flows

None.

## Exception flows

### The task is still `Open`

1. The system refuses and says the task must be started first. See [[03-start-a-task]].
2. Nothing changes.

### The actor is not the executor

1. The system refuses and says only the executor closes their task.
2. Nothing changes.

### The task is already closed or archived

1. The system refuses.
2. Nothing changes.

## Post-conditions

- The task is in state `Closed`, which is final
- The task is finished as soon as the executor closes it
- The task cannot be archived. Finished is not the same as cancelled

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every task in the household, and which are closed | Close a started task only when they are its executor |
| Organizer | Every task in the household, and which are closed | Close a started task only when they are its executor |
| Member | The tasks where they are the requester or the executor | Close a started task they are the executor of |
| Minor member | The tasks where they are the requester or the executor | Close a started task they are the executor of |

## Applied business rules

- [[rules#the-executor-works-the-task]] — nobody closes another member's work
- [[rules#a-task-moves-in-one-direction]] — work is begun before it is finished, so an `Open` task cannot be closed
- [[rules#archiving-ends-a-task-that-was-started]] — a closed task is finished, so it is never archived
