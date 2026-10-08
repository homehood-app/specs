---
status: draft
updated: 2026-10-08
superseded-by:
---

# Remove a member

As a member with organizer authority, I want to remove a member so that the household matches who really lives here.

**Actors:** [[users#owner]], [[users#organizer]], [[users#guardian]]

## Pre-conditions

- The household exists
- The person to remove is a member of it
- The actor has organizer authority in the household, **or** is the guardian of the minor being removed

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

1. The flow is the same, and the account is not touched. The child stops being a member of this household and keeps every other household they belong to.
2. A minor account does not need a household to exist. Only its guardian ends it — see [[accounts/use-cases/03-delete-a-minor-account]].
3. The child cannot do this themselves. This use case is one of the two ways a minor leaves a household, and the other is the same use case with the guardian as the actor. See [[09-leave-a-household]].

### The actor is the guardian of the minor, and has no organizer authority here

1. The guardian can take their child out of a household they are not a member of, and cannot see into. Removing a membership is not reading a household.
2. Step 2 and step 3 do not happen. The guardian is shown nothing of the work and chooses nothing about it.
3. Instead the system tells the guardian that the household may have work of the child's left to settle, without saying what it is or how much.
4. The child's `Open` and `Started` tasks become unresolved and wait for a member with organizer authority in that household. See [[tasks/use-cases/08-resolve-a-former-members-tasks]].

### The actor has organizer authority and is also the guardian

1. They act as a member of the household: they see the work and they resolve it, as in the main flow. Being the guardian takes nothing away.

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

### A guardian tries to remove somebody who is not their minor

1. The system refuses. Guardianship reaches one account and no other member of the household.
2. Nothing changes.

### Organizer authority tries to remove a minor's guardian in order to remove the minor

1. Nothing of the sort happens. The two memberships are separate: removing the guardian from the household leaves the child a member of it.
2. To take the child out as well, the actor removes the child too.

## Post-conditions

- The person is a former member of this household, and sees nothing of it
- Their account is untouched, whatever kind it is. A removed minor keeps their minor account, their guardian, and every other household they belong to
- Every active task the actor resolved has a current member on it, or is archived, or is gone
- Every active task the actor did not resolve, or could not see, is unresolved and waiting
- The person's closed and archived tasks still name them, and are unchanged
- The household still has exactly one owner

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every member, and the active tasks each one is on | Remove any member except themselves, and resolve their tasks in the same step |
| Organizer | Every member, and the active tasks each one is on | Remove any member who is neither the owner nor an organizer, and resolve their tasks in the same step |
| Member | That they are no longer in the household | Nothing. To go, they leave. See [[09-leave-a-household]] |
| Minor | That they are no longer in that household | Nothing. A minor never takes themselves out |
| Guardian | Which households the minor they hold belongs to, and nothing inside the ones they are not a member of | Remove that minor from any of those households. They do not choose where the child's work goes |

## Applied business rules

- [[rules#the-owner-and-the-organizers-decide-who-belongs]] — removal from inside is theirs, and an organizer cannot reach the owner or a peer
- [[rules#a-minors-memberships-are-their-guardians-to-decide]] — the guardian is the second person who can take a minor out, and the account survives it
- [[rules#a-household-is-a-closed-boundary]] — a guardian removes without seeing in
- [[rules#a-household-has-exactly-one-owner-always]] — the owner cannot be removed
- [[rules#a-former-member-stays-on-what-they-left-behind]] — the record of what they did is not rewritten
- [[rules#an-active-task-of-a-former-member-waits-for-organizer-authority]] — the remover may resolve now or leave it for later, and a guardian always leaves it
- [[accounts/rules#only-the-guardian-ends-a-minor-account]] — removal is not deletion
