---
status: draft
updated: 2026-10-07
superseded-by:
---

# Delete a task

As the requester of a task nobody has begun, or as the owner or an organizer, I want to remove a task completely.

**Actors:** [[users#member]], [[users#organizer]], [[users#owner]], [[users#minor-member]]

## Pre-conditions

- The task exists
- The actor is the owner or an organizer, or is the requester of a task that is still `Open`

## Main flow

1. The member selects the task.
2. The system warns that deleting removes the task and its comments, and cannot be undone.
3. The member confirms.
4. The system deletes the task and everything attached to it.

## Alternative flows

### The requester deletes a task nobody started

1. They can. A task that was never begun holds nothing worth keeping.

### The owner or an organizer deletes a started task

1. They can, at any state. Archiving is the gentler option and keeps the history. See [[06-archive-a-task]].

## Exception flows

### The requester tries to delete a task that is already started

1. The system refuses and says the work has begun, so it is archived rather than deleted. See [[06-archive-a-task]].
2. Nothing changes.

### The executor tries to delete a task they did not request

1. The system refuses.
2. Nothing changes.

## Post-conditions

- The task no longer exists
- Its comments no longer exist
- Nobody sees it any more

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every task in the household | Delete any task, in any state |
| Organizer | Every task in the household | Delete any task except one where the owner is the executor |
| Member | The tasks where they are the requester or the executor | Delete a task they requested, while it is still `Open` |
| Minor member | The tasks where they are the requester or the executor | Delete a task they requested, while it is still `Open` |

## Applied business rules

- [[rules#who-can-end-a-task]] — the requester before it starts, the owner and organizers at any time
- [[rules#a-minor-sees-their-own-work-in-full]] — a minor deletes a task they requested while it is still `Open`, the same as a member
- [[rules#archiving-ends-a-task-that-was-started]] — once started, the way out is archiving
- [[rules#an-organizer-cannot-act-on-the-owners-work]] — an organizer stops at the owner
