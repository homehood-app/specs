---
status: draft
updated: 2026-10-08
superseded-by:
---

# Make a minor account a full account

As the guardian of a minor account, I want it to become a full account so that the child holds their own account and keeps everything they did.

**Actors:** [[users#guardian]], [[users#minor]]

## Pre-conditions

- The minor account exists
- The actor is its guardian

## Main flow

1. The guardian asks for the account to become a full account.
2. The system warns that this cannot be undone, and that the guardian will decide nothing about the account afterwards.
3. The guardian confirms.
4. The child, signed in to the account, gives it an email address and a password of its own — see [[05-finish-becoming-a-full-account]].
5. The system makes it a full account.
6. The account has no guardian. Every household it belongs to, every task it is on and every comment it wrote is untouched.

## Alternative flows

### The child does not finish it

1. The account stays a minor account, with the same guardian, until the child finishes step 4.
2. Nothing else changes in the meantime. The child's work goes on exactly as before, with the same handle and the same PIN.
3. The guardian can withdraw the request.

### The child cannot sign in, so cannot reach step 4

1. The guardian issues a new claim code and the child claims the account again — see [[02-sign-in-to-a-minor-account]].
2. The request waits. It does not expire, and the guardian does not have to ask again.
3. The guardian still cannot finish it. Clearing a PIN is not supplying an email address.

### The child belongs to several households

1. Nothing is different. The account keeps the member role in each household, and no household is asked about any of it.
2. The guardian who held the account may be a member of one of those households and not of the others. It makes no difference.

### The household wants the new full account to run things

1. Becoming a full account is not a promotion. The person is still a plain member of each household.
2. The owner of a household promotes them to organizer afterwards, if they want to. See [[household/use-cases/06-change-a-members-role]].

### The child has no household

1. Nothing is different. A minor account with no membership becomes a full account the same way.

## Exception flows

### The actor is not the guardian

1. The system refuses. Only the guardian decides this, and nobody else can ask for it — not an owner, not an organizer, not the child.
2. Nothing changes.

### The account is already a full account

1. The system refuses. There is nothing to change, and a full account never becomes a minor account.
2. Nothing changes.

### The child's half fails

1. Everything that can go wrong in step 4 belongs to [[05-finish-becoming-a-full-account]] — an email address already in use, a withdrawn request, a child who cannot sign in.
2. In every one of them the account stays a minor account, with the same guardian.

## Post-conditions

- The account is a full account, and has no guardian
- It is the same account. Its memberships, its roles, its tasks and its comments are all unchanged and still name the same person
- The former guardian decides nothing about it and sees nothing of it
- The account can now be invited to another household, answer for itself, leave a household, hold any role, and become the guardian of a minor account
- No account can turn it back into a minor account

## By role

Not one household role appears in this table with anything to do. That is the decision: growing up is not a household's to grant.

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | That a member of their household now holds a full account, and can be promoted | Nothing. The owner cannot start this, refuse it, or delay it |
| Organizer | That a member of their household now holds a full account | Nothing |
| Member | Nothing of this use case | Nothing |
| Minor | That their guardian has asked for it, once they sign in | Finish it, in [[05-finish-becoming-a-full-account]]. Nothing happens without them |
| Guardian | The minor accounts they hold, and whether a request is waiting on the child | Ask for a minor account they hold to become a full account, and withdraw the request |

## Applied business rules

- [[rules#a-minor-account-becomes-a-full-account-once]] — who decides, what survives, and that it goes one way
- [[rules#every-minor-account-has-exactly-one-guardian]] — this is one of the three ways guardianship ends
- [[household/rules#a-minor-is-a-member-and-stays-a-member]] — the role does not change here. The account changes kind, not rank
