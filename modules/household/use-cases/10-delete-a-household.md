---
status: draft
updated: 2026-10-07
superseded-by:
---

# Delete a household

As the owner, I want to end the household so that a home we no longer share stops existing.

**Actors:** [[users#owner]]

## Pre-conditions

- The household exists
- The actor is its owner

## Main flow

1. The owner asks to delete the household.
2. The system warns that every task, comment and pending invitation goes with it, and that this cannot be undone.
3. The owner confirms.
4. The system deletes the household and everything inside it.
5. Every member loses access at once.

## Alternative flows

### The household has other members

1. The system says how many members will lose access.
2. The owner confirms anyway, or hands the household on instead. See [[07-transfer-ownership]].

### The household has minors in it

1. The system says that their accounts go with the household. A minor account cannot exist outside the household that made it.
2. A member with a full account keeps their account and every other household they belong to. A minor has neither.

## Exception flows

### The actor is an organizer, not the owner

1. The system refuses and says only the owner deletes the household.
2. Nothing changes.

## Post-conditions

- The household no longer exists
- Its tasks, comments and pending invitations no longer exist
- Nobody is a member of it
- Every minor account the household held no longer exists
- Every member with a full account still has it, and still has their other households

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | The whole household, and how many members it has | Delete it |
| Organizer | That the household is gone | Nothing |
| Member | That the household is gone | Nothing |
| Minor | That the household is gone, and their account with it | Nothing |

## Applied business rules

- [[rules#only-the-owner-changes-the-household-itself]] — ending the household is the owner's alone
- [[rules#a-minor-belongs-to-one-household-and-cannot-leave-it]] — a minor account cannot outlive the household that holds it
