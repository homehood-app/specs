---
status: draft
updated: 2026-10-06
superseded-by:
---

# Remove a member

As the owner or an organizer, I want to remove a member so that the household matches who really lives here.

**Actors:** [[users#owner]], [[users#organizer]]

## Pre-conditions

- The household exists
- The actor is its owner or one of its organizers
- The person to remove is a member of it

## Main flow

1. The actor selects the member to remove.
2. The system shows the tasks where that member is the requester or the executor, and who each one will fall to by default.
3. The actor may hand any of those tasks to a different member instead, or end them.
4. The actor confirms.
5. The system applies the fallback to everything the actor did not redirect, then removes the member.

## Alternative flows

### The member holds no tasks

1. Step 2 and step 3 are skipped.

### The actor accepts every default

1. Step 3 is skipped. The outcome is the same as if the member had left on their own. See [[09-leave-a-household]].

## Exception flows

### The target is the owner

1. The system refuses and says the owner cannot be removed. The owner hands the household on first. See [[07-transfer-ownership]].
2. Nothing changes.

### An organizer tries to remove another organizer

1. The system refuses and says an organizer cannot remove a peer. Only the owner can, after demoting them.
2. Nothing changes.

## Post-conditions

- The person is no longer a member, and sees nothing of the household
- No task in the household keeps the removed person as its requester or its executor
- The household still has exactly one owner

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every member, and the tasks each one holds | Remove any member except themselves |
| Organizer | Every member, and the tasks each one holds | Remove any member who is neither the owner nor an organizer |
| Member | That they are no longer in the household | Nothing. To go, they leave. See [[09-leave-a-household]] |
| Minor member | That they are no longer in the household | Nothing |

## Applied business rules

- [[rules#the-owner-and-the-organizers-decide-who-belongs]] — removal is theirs, and an organizer cannot reach the owner or a peer
- [[rules#a-household-has-exactly-one-owner-always]] — the owner cannot be removed
- [[rules#nobody-is-left-holding-work-they-are-not-there-for]] — where the tasks fall by default, and the actor's freedom to redirect them
