---
status: draft
updated: 2026-10-06
superseded-by:
---

# Archive a task

As the owner of a task, I want to put a finished task away so that my list shows only live work.

**Actors:** [[users#member]], [[users#organizer]], [[users#minor-member]]

## Pre-conditions

- The task exists and is in state `Closed`
- The actor owns it, or the actor is an organizer

## Main flow

1. The owner archives the task.
2. The system sets the task to `Archived`.
3. The task leaves the active lists and stays readable.

## Alternative flows

### An organizer archives it

1. An organizer can archive any closed task in the household, including one they do not own.

## Exception flows

### The task is not closed

1. The system refuses and says only a closed task can be archived.
2. Nothing changes.

### The actor neither owns the task nor is an organizer

1. The system refuses.
2. Nothing changes.

## Post-conditions

- The task is in state `Archived`
- The task is out of the active lists and can still be read
- The task takes no new comments and cannot be edited

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Organizer | Every task in the household, active and archived | Archive any closed task in the household |
| Member | The tasks they own and the tasks they created | Archive a closed task they own |
| Minor member | The tasks they own and the tasks they created | Archive a closed task they own |

## Applied business rules

- [[rules#only-an-organizer-deletes-a-task]] — archiving is the member's way to tidy up, deleting is not
