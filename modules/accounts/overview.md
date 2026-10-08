# Accounts

The account itself: what kinds there are, who is responsible for one, and what happens to it over a life.

An account is not a household concept. It exists before the first household and after the last one, and the same account can be a member of several households at once. That is why this module exists separately from [[household/overview]]: the household owns who belongs to it, and this module owns the thing that belongs.

Almost everything here is about the **minor account**, because it is the only kind somebody else answers for. A full account needs no module: it belongs to the person who made it, and nobody else decides anything about it.

## Actors

- [[users#guardian]] — the one full account responsible for a minor account. Decides where it belongs, when it grows up, and when it ends
- [[users#minor]] — the child whose account it is. Does a member's work in every household, and decides nothing about the account

## Responsibilities

- The two kinds of account, and the one change of kind that is possible
- Guardianship: that every minor account has exactly one guardian, and how guardianship moves
- Making a minor account a full account, and what survives it
- Deleting a minor account
- What a guardian can see and do, and what guardianship does not give them

## Out of scope

- **How a minor account is created, and how a child signs in to it.** Not specified yet. It is the front door of everything in this module, and it is the one part of an account's life that is still open. See [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].
- **How a full account is created, and how its holder signs in.** Ordinary sign-up. Not specified yet either, and not urgent — nothing in the product depends on the detail.
- **How a full account is deleted.** Not specified yet. What is already settled is the part that touches this module: a guardian cannot leave a minor account behind. See [[rules#every-minor-account-has-exactly-one-guardian]].
- **Membership of a household, and the authority that comes with it.** See [[household/overview]]. An invitation is a household act, even the one a guardian answers.
- **The work.** See [[tasks/overview]]. Guardianship gives no authority over a task.

## Related modules

- [[household/overview]] — a membership is a household's to grant and a guardian's to accept. Removal belongs to both
- [[tasks/overview]] — a minor's work is a member's work, and a guardian has no part in it

## Use cases

[[use-cases/index]]

## Business rules

[[rules]]
