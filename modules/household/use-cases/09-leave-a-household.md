---
status: draft
updated: 2026-10-07
superseded-by:
---

# Leave a household

As a member, I want to take myself out of a household so that I am not in a home I no longer share.

**Actors:** [[users#member]], [[users#organizer]], [[users#minor-member]], [[users#owner]]

## Pre-conditions

- The actor is a member of the household
- The actor is not its owner

## Main flow

1. The member asks to leave.
2. The system shows how many active tasks they are on, and says those will wait for a member with organizer authority to decide.
3. The member confirms.
4. The system removes the member from the household. They are now a former member.
5. Their `Open` and `Started` tasks become unresolved and wait. Their `Closed` and `Archived` tasks are untouched, and still name them.

## Alternative flows

### The member is on no active tasks

1. Step 2 is skipped. There is nothing to resolve.

### The owner wants to leave

1. The owner hands the household to another member first. See [[07-transfer-ownership]].
2. They are then an organizer, and leave by this use case.

## Exception flows

### The actor is the owner and the only member

1. The system refuses and says the household must be deleted instead. See [[10-delete-a-household]].
2. Nothing changes.

## Post-conditions

- The person is a former member, and sees nothing of the household
- Their active tasks are unresolved, and waiting. See [[tasks/use-cases/08-resolve-a-former-members-tasks]]
- Their closed and archived tasks still name them, and are unchanged
- Every comment they wrote is unchanged
- The household still has exactly one owner

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | The households they belong to | Nothing here. Hand the household on first, then leave as an organizer |
| Organizer | The households they belong to, and how many active tasks they are on | Leave. They do not choose where their tasks go |
| Member | The households they belong to, and how many active tasks they are on | Leave. They do not choose where their tasks go |
| Minor member | The households they belong to, and how many active tasks they are on | Leave. They do not choose where their tasks go |

## Applied business rules

- [[rules#a-household-has-exactly-one-owner-always]] — the owner cannot leave while they hold the household
- [[rules#a-former-member-stays-on-what-they-left-behind]] — the record of what they did is not rewritten
- [[rules#an-active-task-of-a-former-member-waits-for-organizer-authority]] — the leaver does not redistribute the household's work
