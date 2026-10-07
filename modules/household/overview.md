# Household

The household itself: what it is, who belongs to it, and who may act on whom inside it.

This module owns the boundary every other module depends on. A task, a comment and an invitation are all inside exactly one household, and a person who is not a member of that household cannot reach any of them.

## Actors

- [[users#owner]] — holds the household, and is the only member who can change it
- [[users#organizer]] — runs the household's day-to-day membership
- [[users#member]] — belongs to the household
- [[users#minor-member]] — a member under the care of the household, who sees the people but not their roles

## Responsibilities

- Creating a household, editing it and deleting it
- Who holds the household, and handing that on
- Inviting a person, revoking an invitation, and answering one
- Changing a member's role
- Removing a member, and leaving on your own
- What becomes of a former member's tasks and comments
- What a minor member sees of the household, and who takes a minor out of it

## Out of scope

- Everything about the household's work. See [[tasks/overview]]. A minor's authority over the work is a member's, in full — see [[decisions/0006-a-minor-is-reduced-on-the-household-not-on-the-work]].

## Related modules

- [[tasks/overview]] — every task belongs to a household, and its requester and executor are members of it

## Use cases

[[use-cases/index]]

## Business rules

[[rules]]
