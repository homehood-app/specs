---
status: draft
updated: 2026-10-07
superseded-by:
---

# Remove a member

As a member with organizer authority, I want to remove a member so that the household matches who really lives here.

**Actors:** [[users#owner]], [[users#organizer]]

## Pre-conditions

- The household exists
- The actor has organizer authority in it
- The person to remove is a member of it

## Main flow

1. The actor selects the member to remove.
2. The system shows the active tasks that member is on.
3. The actor decides, per task: give it to another member, archive it, or delete it. The actor can also discard the lot, or leave them all for later.
4. The actor confirms.
5. The system applies the choices and removes the member. They are now a former member.

## Alternative flows

### The member is on no active tasks

1. Step 2 and step 3 are skipped.

### The member is a minor

1. The flow is the same, with one consequence: a minor account cannot exist outside a household, so the account ends with the membership.
2. This is the only way a minor leaves a household. A minor cannot leave on their own. See [[09-leave-a-household]].
3. The system says so before step 4. Removing a minor is not the same as removing a member who keeps their account and their other households.
4. What the child did stays on the household's record, as it does for any former member.

### The actor discards the lot

1. The system archives every `Started` task and deletes every `Open` one.

### The actor leaves them for later

1. The tasks become unresolved, exactly as if the member had left on their own.
2. Anybody with organizer authority finishes the job later. See [[tasks/use-cases/08-resolve-a-former-members-tasks]].

## Exception flows

### The target is the owner

1. The system refuses and says the owner cannot be removed. The owner hands the household on first. See [[07-transfer-ownership]].
2. Nothing changes.

### An organizer tries to remove another organizer

1. The system refuses and says an organizer cannot remove a peer. Only the owner can, after demoting them.
2. Nothing changes.

## Post-conditions

- The person is a former member, and sees nothing of the household
- A removed minor's account no longer exists. A removed member with a full account keeps it, and keeps every other household they belong to
- Every active task the actor resolved has a current member on it, or is archived, or is gone
- Every active task the actor did not resolve is unresolved, and waiting
- The person's closed and archived tasks still name them, and are unchanged
- The household still has exactly one owner

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every member, and the active tasks each one is on | Remove any member except themselves, and resolve their tasks in the same step |
| Organizer | Every member, and the active tasks each one is on | Remove any member who is neither the owner nor an organizer, and resolve their tasks in the same step |
| Member | That they are no longer in the household | Nothing. To go, they leave. See [[09-leave-a-household]] |
| Minor | That they are no longer in the household | Nothing. This use case is the only way a minor leaves, and their account ends with it |

## Applied business rules

- [[rules#the-owner-and-the-organizers-decide-who-belongs]] — removal is theirs, and an organizer cannot reach the owner or a peer
- [[rules#a-minor-belongs-to-one-household-and-cannot-leave-it]] — a minor goes out by this use case and no other, and the account ends with the membership
- [[rules#a-household-has-exactly-one-owner-always]] — the owner cannot be removed
- [[rules#a-former-member-stays-on-what-they-left-behind]] — the record of what they did is not rewritten
- [[rules#an-active-task-of-a-former-member-waits-for-organizer-authority]] — the remover may resolve now or leave it for later
