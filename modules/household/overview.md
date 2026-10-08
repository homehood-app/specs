# Household

The household itself: what it is, who belongs to it, and who may act on whom inside it.

This module owns the boundary every other module depends on. A task, a comment and an invitation are all inside exactly one household, and a person who is not a member of that household cannot reach any of them.

## Actors

- [[users#owner]] — holds the household, and is the only member who can change it
- [[users#organizer]] — runs the household's day-to-day membership
- [[users#member]] — belongs to the household
- [[users#minor]] — a child who is a member here. A member who did not choose to join and cannot leave or be promoted
- [[users#guardian]] — the account responsible for a minor. Not a member by being one. Answers the invitation that brings the child in, and can take them out again

## Responsibilities

- Creating a household, editing it and deleting it
- Who holds the household, and handing that on
- Inviting a person, revoking an invitation, and answering one
- Changing a member's role
- Removing a member, and leaving on your own
- What becomes of a former member's tasks and comments
- What a minor can and cannot do inside the household, and who takes a minor out of it

## Out of scope

- Everything about the household's work. See [[tasks/overview]]. A minor's authority over the work is a member's, in full — see [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].
- The life of an account: the two kinds, guardianship, growing up, and deletion. See [[accounts/overview]]. A household grants and ends a membership; it decides nothing about the account behind it, not even a child's.
- How a minor account is created, and how a child signs in to it. Not specified yet — see [[accounts/overview]].

## Related modules

- [[tasks/overview]] — every task belongs to a household, and its requester and executor are members of it
- [[accounts/overview]] — a membership belongs to an account. For a minor, the guardian answers the invitation and can end the membership from outside

## Use cases

[[use-cases/index]]

## Business rules

[[rules]]
