---
status: draft
updated: 2026-10-06
superseded-by:
---

# Delete a task

As an organizer, I want to remove a task completely so that the household is not carrying work that should never have been there.

**Actors:** [[users#organizer]]

## Pre-conditions

- The task exists in the household
- The actor is an organizer of that household

## Main flow

1. The organizer selects the task.
2. The system warns that deleting removes the task and its comments, and cannot be undone.
3. The organizer confirms.
4. The system deletes the task and everything attached to it.

## Alternative flows

### The task is in any state

1. The organizer can delete a task that is `Open`, `Started`, `Closed` or `Archived`.

## Exception flows

### The actor is not an organizer

1. The system refuses and says only an organizer deletes a task.
2. Nothing changes.

## Post-conditions

- The task no longer exists
- Its comments no longer exist
- The owner and the creator no longer see it

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Organizer | Every task in the household | Delete any task in the household |
| Member | The tasks they own and the tasks they created | Nothing. A member cannot delete a task, not even their own. They archive it instead |
| Minor member | The tasks they own and the tasks they created | Nothing. They archive instead |

## Applied business rules

- [[rules#only-an-organizer-deletes-a-task]] — deleting is the organizer's authority alone
