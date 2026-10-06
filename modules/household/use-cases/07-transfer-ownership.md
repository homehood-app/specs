---
status: draft
updated: 2026-10-06
superseded-by:
---

# Transfer ownership

As the owner, I want to hand the household to another member so that somebody else holds it.

**Actors:** [[users#owner]]

## Pre-conditions

- The household exists and has at least two members
- The actor is its owner

## Main flow

1. The owner selects the member who will take the household.
2. The system warns that the change cannot be undone by the current owner alone.
3. The owner confirms.
4. The system makes the chosen member the owner.
5. The system makes the previous owner an organizer.

## Alternative flows

### The previous owner wants to leave as well

1. They leave the household afterwards. See [[09-leave-a-household]].

## Exception flows

### The household has only one member

1. The system refuses and says there is nobody to hand it to.
2. Nothing changes.

### The actor is not the owner

1. The system refuses.
2. Nothing changes.

## Post-conditions

- The chosen member is the owner
- The previous owner is an organizer, and still a member
- The household has exactly one owner
- No task changed its requester or its executor

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every member of the household | Hand the household to any other member, and become an organizer |
| Organizer | Who the owner is | Nothing. An organizer cannot take the household |
| Member | Who the owner is | Nothing. A member can receive the household but cannot ask for it |
| Minor member | Who the owner is | Nothing |

## Applied business rules

- [[rules#only-the-owner-changes-the-household-itself]] — handing the household on is the owner's alone
- [[rules#a-household-has-exactly-one-owner-always]] — the household is never without an owner, not even for a moment
