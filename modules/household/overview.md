# Household

The household itself: who belongs to it, and how people join and leave it.

This module owns the boundary that every other module depends on. A task, a comment and an invitation are all inside exactly one household, and a person who is not a member of that household cannot reach any of them.

## Actors

- [[users#organizer]] — creates the household, invites people, removes members
- [[users#member]] — accepts an invitation and belongs to the household
- [[users#minor-member]] — a member under the care of an organizer

## Responsibilities

- Creating a household
- Inviting a person to a household, and the state of that invitation
- Accepting an invitation, which is the only way to become a member
- Removing a member from a household

## Out of scope

- Everything about the household's work. See [[tasks/overview]].
- Promoting a member to organizer. [[users]] says an organizer is created or promoted, but promotion is not specified yet.
- A member who is not an organizer leaving on their own initiative. Not specified yet.

## Related modules

- [[tasks/overview]] — every task belongs to a household and is owned by one of its members

## Use cases

[[use-cases/index]]

## Business rules

[[rules]]
