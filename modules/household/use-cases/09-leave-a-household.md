---
status: draft
updated: 2026-10-06
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
2. The system shows the tasks where they are the requester or the executor.
3. The member confirms.
4. The system hands those tasks to the owner and removes the member.

## Alternative flows

### The member holds no tasks

1. Step 2 is skipped.

### The owner wants to leave

1. The owner hands the household to another member first. See [[07-transfer-ownership]].
2. They are then an organizer, and leave by this use case.

## Exception flows

### The actor is the owner and the only member

1. The system refuses and says the household must be deleted instead. See [[10-delete-a-household]].
2. Nothing changes.

## Post-conditions

- The person is no longer a member, and sees nothing of the household
- No task in the household keeps the departed person as its requester or its executor
- The household still has exactly one owner

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | The households they belong to | Nothing here. Hand the household on first, then leave as an organizer |
| Organizer | The households they belong to | Leave |
| Member | The households they belong to | Leave |
| Minor member | The households they belong to | Leave |

## Applied business rules

- [[rules#a-household-has-exactly-one-owner-always]] — the owner cannot leave while they hold the household
- [[rules#nobody-is-left-holding-work-they-are-not-there-for]] — the leaver's tasks go to the owner
