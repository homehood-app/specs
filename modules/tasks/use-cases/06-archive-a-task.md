---
status: draft
updated: 2026-10-06
superseded-by:
---

# Archive a task

As a member who can see a started task that will not be finished, I want to end it without losing what it holds.

**Actors:** [[users#member]], [[users#organizer]], [[users#owner]], [[users#minor-member]]

## Pre-conditions

- The task exists and is in state `Started`
- The actor is its executor, its requester, the owner, or an organizer

## Main flow

1. The member says the task will not be finished, and gives the reason.
2. The system sets the task to `Archived`.
3. The task leaves the active lists, and stays readable with everything on it — its comments, who started it, and when.

## Alternative flows

### The work is wanted again later

1. A new task is created for it. An archived task is not reopened.

## Exception flows

### The task was never started

1. The system refuses and says a task that was never started is deleted instead. See [[07-delete-a-task]].
2. Nothing changes.

### The task is closed

1. The system refuses and says a finished task is not abandoned.
2. Nothing changes.

## Post-conditions

- The task is in state `Archived`, which is final
- The task and its comments are still readable
- The task takes no new comments and cannot be edited, started or closed

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every task in the household, active and archived | Archive any started task |
| Organizer | Every task in the household, active and archived | Archive any started task except one where the owner is the executor |
| Member | The tasks where they are the requester or the executor | Archive a started task of theirs |
| Minor member | The tasks where they are the requester or the executor | Archive a started task of theirs |

## Applied business rules

- [[rules#archiving-ends-a-task-that-was-started]] — only a started task is archived, and it is kept for what it holds
- [[rules#who-can-end-a-task]] — who may do it
- [[rules#an-organizer-cannot-act-on-the-owners-work]] — an organizer stops at the owner
