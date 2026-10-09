---
status: draft
updated: 2026-10-08
superseded-by:
---

# Transfer guardianship

As the guardian of a minor account, I want to hand it to another person so that somebody else is responsible for the child's account.

**Actors:** [[users#guardian]]

## Pre-conditions

- The minor account exists
- The actor is its guardian
- The person who will take it holds a full account

## Main flow

1. The guardian chooses the minor account and the full account that will take it.
2. The system warns that the guardian loses every decision over the account, including the right to take it back.
3. The guardian confirms.
4. The system offers guardianship to the chosen account.
5. The chosen account accepts.
6. The system makes them the guardian. The previous guardian is no longer one.

## Alternative flows

### The chosen account declines, or never answers

1. Nothing changes. The actor is still the guardian.
2. The offer can be withdrawn, and another one made to somebody else.

### The two people share a household with the child

1. Nothing is different. Guardianship and membership have nothing to do with each other, and neither one moves the other.

### The new guardian is in none of the child's households

1. Nothing is different. A guardian never has to be a member of a household the minor belongs to.
2. The new guardian sees which households the child belongs to, and nothing inside the ones they are not a member of.

## Exception flows

### The chosen account is a minor account

1. The system refuses and says a guardian holds a full account.
2. Nothing changes.

### The chosen account is already the guardian

1. The system refuses. There is nothing to transfer.
2. Nothing changes.

### The actor is not the guardian

1. The system refuses. Nobody but the guardian hands the account on, and nobody can take it from them.
2. Nothing changes.

## Post-conditions

- The minor account has exactly one guardian, and it is the chosen account
- The previous guardian decides nothing about the account any more, and sees nothing of it
- Every household the minor belongs to is unchanged, and so is the minor's role in each one
- No task changed its requester or its executor
- The minor's own view of their work did not change

## By role

The three household roles have no part in this. Guardianship sits outside every household, which is the point of it.

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Nothing of this use case. A household cannot stop it, delay it, or be asked about it | Nothing |
| Organizer | Nothing of this use case | Nothing |
| Member | Nothing of this use case | Nothing |
| Minor | Who their guardian is | Nothing. Who holds the account is not the child's to decide |
| Guardian | The minor accounts they hold, and any offer of guardianship made to them | Hand a minor account they hold to any full account, and accept or decline an offer of one |

## Applied business rules

- [[rules#every-minor-account-has-exactly-one-guardian]] — there is one guardian before and one after, and never none in between
- [[rules#a-guardian-decides-the-account-not-the-household]] — what moves is authority over the account, and nothing inside any home
