---
status: draft
updated: 2026-10-07
superseded-by:
---

# Resolve a former member's tasks

As a member with organizer authority, I want to decide what happens to the active tasks of somebody who has left so that the household's work does not sit waiting on a person who is gone.

**Actors:** [[users#owner]], [[users#organizer]]

## Pre-conditions

- The household has at least one unresolved task: an `Open` or `Started` task whose requester or executor is a former member
- The actor has organizer authority in that household

## Main flow

1. The actor opens the household's unresolved tasks.
2. For each one, the system shows what it is, its state, and which side of it the former member held.
3. The actor chooses, per task: give it to another member, archive it, or delete it.
4. The system applies each choice.

## Alternative flows

### The actor resolves all of them at once

1. The actor chooses to discard the lot.
2. The system archives every `Started` task and deletes every `Open` one.
3. Nothing is handed to a member who did not ask for it.

### The actor gives a task to another member

1. The actor names a member of the household as the new executor, the new requester, or both.
2. If the task was `Started` and the executor changed, it returns to `Open`. Nobody inherits work already begun.

### The actor leaves them for later

1. The tasks stay unresolved. They keep waiting, and they are not lost.

### The former member comes back

1. They are invited and accept again, as a new membership. Their old tasks do not return to them on their own. An unresolved task is still resolved by this use case.

## Exception flows

### The chosen member is not a member of the household

1. The system refuses and says the person is not in this household.
2. That task stays unresolved.

### The task is `Open` and the actor tries to archive it

1. The system refuses and says a task that was never started is deleted instead.
2. That task stays unresolved.

### A plain member opens the list

1. The system shows them nothing. Resolving is organizer authority.

### A minor is on one of the unresolved tasks

1. Nothing is different. A minor sees their unresolved task and that it waits, like any member.
2. A minor whose task is given to somebody else stops seeing it, like any member who is no longer on it.

### The tasks are waiting because a guardian took the child out

1. Nothing is different, and this is the ordinary way a minor's work ends up here. A guardian sees nothing inside the household, so they settle nothing — see [[household/use-cases/08-remove-a-member]].
2. The child's guardian is not consulted and cannot be. The work belongs to the household.

## Post-conditions

- Every task the actor resolved either has a requester and an executor who are current members, or is `Archived`, or no longer exists
- A task the actor did not resolve is still unresolved, and still waits
- No `Closed` or `Archived` task was touched. The record of what the former member did is intact
- Every comment the former member wrote is intact

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every unresolved task in the household | Give any of them to a member, archive a started one, delete any, or resolve all at once |
| Organizer | Every unresolved task in the household | The same, except on a task where the owner is the requester or the executor |
| Member | Only an unresolved task they are still on themselves | Nothing. Resolving is organizer authority |
| Minor | Only an unresolved task they are still on themselves | Nothing |

## Applied business rules

- [[rules#an-unresolved-task-is-a-task-with-a-former-member-on-it]] — what is unresolved, and who resolves it
- [[rules#a-minor-works-like-any-other-member]] — a minor is on the list exactly as a member is
- [[rules#a-task-moves-in-one-direction]] — a started task is archived, an open one is deleted
- [[rules#an-organizer-cannot-act-on-the-owners-work]] — an organizer stops at the owner
