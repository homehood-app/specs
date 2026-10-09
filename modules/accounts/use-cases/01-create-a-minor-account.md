---
status: draft
updated: 2026-10-08
superseded-by:
---

# Create a minor account

As the holder of a full account, I want to make an account for a child so that they can take part in a household's routine and I answer for the account.

**Actors:** [[users#member]], [[users#guardian]], [[users#minor]]

## Pre-conditions

- The actor holds a full account
- The actor is signed in

## Main flow

1. The actor asks to make an account for a child.
2. The actor gives the child's **name**, and a **handle** for the account.
3. The actor may give a picture. Nothing else is asked — no email address, and no date of birth.
4. The system creates a minor account and makes the actor its **guardian**.
5. The system issues a **claim code** for the account and shows it to the guardian, once, to give to the child.
6. The account exists, holds no membership, and is waiting to be claimed. See [[02-sign-in-to-a-minor-account]].

## Alternative flows

### The actor belongs to no household

1. Nothing is different. An account is not a household concept, so no household has to exist first — see [[overview]].
2. The account can be invited into a household later, like any other, and the guardian answers that invitation.

### The actor wants the child in their own household

1. Making the account does not put the child in it. The guardian invites the account afterwards, and answers their own invitation — see [[household/use-cases/03-invite-a-person]].
2. An invitation is the one door into a household, for every kind of account — see [[household/rules#membership-starts-with-an-accepted-invitation]].

### The handle is already taken

1. The system refuses the handle and proposes one that is free. A handle is unique across the whole product.
2. The actor takes the proposal or gives another handle. Nothing else they typed is lost.

### The actor already holds minor accounts

1. Nothing is different. One guardian holds as many minor accounts as they have children — see [[rules#every-minor-account-has-exactly-one-guardian]].
2. Each account has its own name, its own handle and its own claim code.

### Two children have the same name

1. Nothing is refused. A name is not an identifier, and two accounts can carry the same name.
2. Their handles are different, because a handle is unique.

### The guardian loses the claim code before the child uses it

1. The code is shown once and is not shown again.
2. The guardian issues a new one. See [[02-sign-in-to-a-minor-account]].

## Exception flows

### The actor holds a minor account

1. The system refuses. A minor account cannot be a guardian, so a child cannot make an account for another child — see [[rules#every-minor-account-has-exactly-one-guardian]].
2. Nothing is created.

### The actor gives no name, or no handle

1. The system refuses and says which one is missing. Both are required.
2. Nothing is created.

## Post-conditions

- A minor account exists, with a name, a handle, and a picture if one was given
- The actor is its guardian, and is the only account that is
- The account holds no email address and no password
- The account belongs to no household
- A claim code is waiting for the child, and the account cannot be signed in to until the child uses it

## By role

Making a minor account is not a household act, so no household role appears here with anything to do. The actor may happen to be an owner; it makes no difference.

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Nothing of this use case. A child who is not yet invited is not theirs to see | Nothing as owner. As the holder of a full account, make a minor account like anybody else |
| Organizer | Nothing of this use case | Nothing as organizer. As the holder of a full account, make a minor account like anybody else |
| Member | Nothing of this use case | As the holder of a full account, make a minor account and become its guardian |
| Minor | Nothing. The child has no account until it is made, and reaches it in [[02-sign-in-to-a-minor-account]] | Nothing. A minor account cannot make another |
| Guardian | The minor accounts they hold, each with its name, its handle, and whether it has been claimed | Make another minor account, which they also become the guardian of |

## Applied business rules

- [[rules#a-guardian-issues-the-way-in-and-can-issue-it-again]] — the handle, the claim code, and who holds each
- [[rules#an-account-holds-a-name-a-handle-and-a-picture]] — what is asked for, and what is deliberately not
- [[rules#every-minor-account-has-exactly-one-guardian]] — the maker becomes the guardian, and a minor cannot be one
- [[household/rules#membership-starts-with-an-accepted-invitation]] — this does not make the child a member of anything
