# Accounts

The account itself: what kinds there are, who is responsible for one, and what happens to it over a life.

An account is not a household concept. It exists before the first household and after the last one, and the same account can be a member of several households at once. That is why this module exists separately from [[household/overview]]: the household owns who belongs to it, and this module owns the thing that belongs.

The module covers **both kinds of account**, full and minor, for the whole of their lives. What is written here so far is only the minor-account part, because that is the part the product has decided. The full-account half is this module's too and is not specified yet, and the list below says which pieces are missing rather than leaving a reader to guess.

## Actors

- [[users#member]] — anybody holding a full account. Signs themselves up, holds their own account, and answers for nobody else
- [[users#guardian]] — the one full account responsible for a minor account. Decides where it belongs, when it grows up, and when it ends
- [[users#minor]] — the child whose account it is. Does a member's work in every household, and decides nothing about the account

## Responsibilities

- The two kinds of account, and the one change of kind that is possible
- Creating an account, of either kind, and signing in to one. A child does it with a handle, a claim code and a PIN — see [[domain]]
- What an account holds about the person, and who can change it
- Ending an account, of either kind
- Guardianship: that every minor account has exactly one guardian, and how guardianship moves
- Making a minor account a full account, and what survives it
- What a guardian can see and do, and what guardianship does not give them

## Owned here, not specified yet

These are this module's to answer. Nothing below is settled, and nothing below should be inferred from what is written.

- **Signing up for a full account, and signing in to one.** The ordinary front door, and still open. The minor front door is answered and is a different question — see [[decisions/0014-a-child-signs-in-with-a-handle-and-a-pin]].
- **What a full account holds about the person** — a name, a picture, anything else — and who may change it. What a *minor* account holds is settled: see [[rules#an-account-holds-a-name-a-handle-and-a-picture]].
- **Deleting a full account.** One part of it is already settled, because it touches guardianship: a guardian cannot leave a minor account behind. See [[rules#every-minor-account-has-exactly-one-guardian]]. The rest is open.
- **Whether a deleted full account can come back.** A deleted minor account cannot — see [[rules#only-the-guardian-ends-a-minor-account]].

## Out of scope

- **Membership of a household, and the authority that comes with it.** See [[household/overview]]. An invitation is a household act, even the one a guardian answers.
- **The work.** See [[tasks/overview]]. Guardianship gives no authority over a task.

## Related modules

- [[household/overview]] — a membership is a household's to grant and a guardian's to accept. Removal belongs to both
- [[tasks/overview]] — a minor's work is a member's work, and a guardian has no part in it

## Use cases

[[use-cases/index]]

## Business rules

[[rules]]
