---
status: draft
updated: 2026-10-08
superseded-by:
---

# Finish becoming a full account

As a child whose guardian has asked for it, I want to give my account an email address and a password of my own so that the account becomes mine and nobody answers for me.

**Actors:** [[users#minor]], [[users#guardian]]

## Pre-conditions

- The account is a minor account
- Its guardian has asked for it to become a full account — see [[04-make-a-minor-account-a-full-account]]
- The child is signed in to the account — see [[02-sign-in-to-a-minor-account]]

## Main flow

1. The child, signed in, sees that their guardian has asked for the account to become a full account.
2. The system tells the child what changes: they will decide everything about the account, their guardian will decide nothing, and they will sign in with the email address instead of the handle.
3. The child gives an **email address** and a **password**.
4. The system makes it a full account.
5. The account has no guardian. The handle and the PIN stop working, and the claim code is gone with them.
6. Every household the account belongs to, every task it is on and every comment it wrote is untouched.

## Alternative flows

### The child does not want to yet

1. The child does nothing. The account stays a minor account, with the same guardian, and the child's work goes on exactly as before.
2. Nothing expires. The request waits until the child acts or the guardian withdraws it.

### The child belongs to several households

1. Nothing is different. One account, one upgrade, and no household is asked — see [[rules#a-minor-account-becomes-a-full-account-once]].
2. The child keeps the member role in each one.

### The child cannot sign in, so cannot finish it

1. The child asks their guardian for a new claim code, claims the account again, and finishes from inside it — see [[02-sign-in-to-a-minor-account]].
2. The guardian cannot finish it on the child's behalf. Starting it and finishing it are two different acts by two different people.

### The child wants to keep their handle

1. They cannot. A full account is reached by its email address, and the handle is released.
2. The account is still the same account, under the same name, holding everything it held.

## Exception flows

### The email address already belongs to another account

1. The system refuses and asks for another one. The account stays a minor account, with the same guardian.
2. Nothing else the child typed is lost.

### The guardian has not asked for it

1. The system refuses. A child does not decide that their own account becomes a full one — see [[users#minor]].
2. The child cannot ask for it either, and asking is not a thing the product offers them. They ask their guardian in person.

### The guardian withdraws the request while the child is finishing it

1. The account stays a minor account. The handle and the PIN keep working.
2. The child is told the request is gone. Nothing they gave is kept.

### The account is already a full account

1. The system refuses. There is nothing left to finish, and a full account never becomes a minor account.

## Post-conditions

- The account is a full account, with an email address and a password of its own, and no guardian
- Its handle and its PIN no longer work, and the handle is free for another account
- It is the same account: its memberships, its roles, its tasks and its comments all still name the same person
- The former guardian decides nothing about it and sees nothing of it
- The person can now answer for themselves, leave a household, hold any role, and be the guardian of a minor account

## By role

This is the one act in the product that only the child can do. No household role appears with anything to do, and the guardian's part is already over.

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | That a member of their household now holds a full account, and can be promoted | Nothing. The owner cannot start this, finish it, refuse it, or delay it |
| Organizer | That a member of their household now holds a full account | Nothing |
| Member | Nothing of this use case | Nothing |
| Minor | That their guardian has asked for it, and what it will change | Finish it, by giving an email address and a password while signed in. Or leave it waiting |
| Guardian | That the request is waiting on the child, and that it finished | Withdraw the request. Nothing else. They cannot supply the email address or the password |

## Applied business rules

- [[rules#a-minor-account-becomes-a-full-account-once]] — who decides, what survives, and that the child finishes it
- [[rules#a-guardian-issues-the-way-in-and-can-issue-it-again]] — the handle and the PIN end here, and the child must be signed in to act
- [[rules#every-minor-account-has-exactly-one-guardian]] — this is one of the three ways guardianship ends
- [[household/rules#a-minor-is-a-member-and-stays-a-member]] — the role does not change. The account changes kind, not rank
