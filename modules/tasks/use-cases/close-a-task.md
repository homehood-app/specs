---
status: draft
updated: 2026-10-06
superseded-by:
---

# Close a task

As the owner of a task, I want to say the work is finished so that nobody has to ask.

**Actors:** [[users#member]], [[users#organizer]], [[users#minor-member]]

## Pre-conditions

- The task exists and is in state `Open` or `Started`
- The actor owns it

## Main flow

1. The owner closes the task.
2. The system sets the task to `Closed`.
3. The creator and every organizer see that it is closed.

## Alternative flows

### The task was never started

1. The system closes it anyway. Going through `Started` is not required.

## Exception flows

### The actor does not own the task

1. The system refuses and says only the owner closes their task.
2. Nothing changes.

### The task is already closed or archived

1. The system refuses.
2. Nothing changes.

## Post-conditions

- The task is in state `Closed`
- The task is closed as soon as the owner closes it

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Organizer | Every task in the household, and which are closed | Close a task only if they own it |
| Member | The tasks they own and the tasks they created | Close a task they own |
| Minor member | The tasks they own and the tasks they created | Close a task they own |

## Applied business rules

- [[rules#the-owner-works-the-task]] — only the owner closes it
