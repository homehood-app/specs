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
2. The system shows the tasks where they are the requester or the executor, and who each one will fall to.
3. The member confirms.
4. The system hands each task on by the fallback in [[rules#nobody-is-left-holding-work-they-are-not-there-for]].
5. The system removes the member from the household.

## Alternative flows

### The member holds no tasks

1. Step 2 is skipped.

### A task the member was executing was requested by somebody else

1. The requester becomes the executor. They asked for the work, so they are the one who still wants it.
2. If the task was `Started`, it returns to `Open`. Nobody inherits work already begun.

### A task the member requested is being executed by somebody else

1. The executor keeps it.
2. The owner becomes the requester.

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
- Every task that was theirs has a requester and an executor who are still members
- The household still has exactly one owner

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | The households they belong to | Nothing here. Hand the household on first, then leave as an organizer |
| Organizer | The households they belong to, and where their tasks will fall | Leave |
| Member | The households they belong to, and where their tasks will fall | Leave |
| Minor member | The households they belong to, and where their tasks will fall | Leave |

## Applied business rules

- [[rules#a-household-has-exactly-one-owner-always]] — the owner cannot leave while they hold the household
- [[rules#nobody-is-left-holding-work-they-are-not-there-for]] — where each of the leaver's tasks goes, and why the leaver does not choose
