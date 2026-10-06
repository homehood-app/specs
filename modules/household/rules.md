# Household — Business Rules

## Authority over members runs owner, organizer, member

- The owner can act on any member
- An organizer can act on any member who is neither the owner nor another organizer
- A member can act on nobody but themselves

This rule is about acting on *people*. Asking another member for work is not acting on them — see [[tasks/rules#any-member-can-request-work-from-any-member]].

## Only the owner changes the household itself

- Only the owner edits the household data
- Only the owner changes a member's role
- Only the owner hands ownership to another member
- Only the owner deletes the household

## The owner and the organizers decide who belongs

- An owner or an organizer can invite a person
- An owner or an organizer can revoke a pending invitation
- An organizer cannot remove the owner, and cannot remove another organizer

## Membership starts with an accepted invitation

There is no other way into a household.

- A person is not a member while their invitation is `Pending`
- A person is not a member if their invitation is `Declined` or `Revoked`

## A household has exactly one owner, always

- The owner cannot leave or be removed while they are the owner
- To leave, the owner hands ownership to another member first, or deletes the household

## Nobody is left holding work they are not there for

- When a member leaves a household, by any route, no task in that household may keep them as its requester or its executor

## A household is a closed boundary

- A person who is not a member of a household cannot see or change anything inside it
- A person can be a member of any number of households at the same time
