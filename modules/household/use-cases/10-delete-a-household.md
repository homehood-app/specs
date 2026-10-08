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

1. Nothing is different. Their accounts do not go with the household: a minor account needs no household to exist, and only its guardian ends it. See [[accounts/rules#only-the-guardian-ends-a-minor-account]].
2. Each child stops being a member of this household and keeps every other household they belong to. A child who belonged only to this one keeps the account with no household at all, and their guardian still holds it.
3. The owner is deleting a home, not a person's account. The owner of a household has no power over a child's account, even a child in it.

## Exception flows

### The actor is an organizer, not the owner

1. The system refuses and says only the owner deletes the household.
2. Nothing changes.

## Post-conditions

- The household no longer exists
- Its tasks, comments and pending invitations no longer exist
- Nobody is a member of it
- Every account that was a member still exists, whatever kind it is, and still has its other households
- Every minor account that was a member still has the same guardian

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | The whole household, and how many members it has | Delete it |
| Organizer | That the household is gone | Nothing |
| Member | That the household is gone | Nothing |
| Minor | That the household is gone. Their account is not | Nothing |
| Guardian | That the minor they hold is in one household fewer | Nothing. A guardian can neither cause this nor stop it |

## Applied business rules

- [[rules#only-the-owner-changes-the-household-itself]] — ending the household is the owner's alone
- [[rules#a-minors-memberships-are-their-guardians-to-decide]] — a minor account outlives the household, and loses one membership
- [[accounts/rules#only-the-guardian-ends-a-minor-account]] — an owner deleting a home does not delete a child's account
