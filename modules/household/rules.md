# Household — Business Rules

## Authority over members runs owner, organizer, member, minor

- The owner can act on any member
- An organizer can act on any member who is neither the owner nor another organizer
- A member can act on nobody but themselves
- A minor can act on nobody but themselves

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

When a member leaves a household, by any route, no task in that household may keep them as its requester or its executor. Each of their tasks falls back to somebody who is still there:

- A task they were executing, that somebody else requested, goes to its requester as the new executor
- A task they requested, that somebody else is executing, keeps its executor and goes to the owner as the new requester
- A task where they were both the requester and the executor goes to the owner as both

The fallback is a default, not a ceiling. Whoever removes a member may hand any of their tasks to a different member first. A member who leaves on their own does not choose — redistributing the household's work is the household's call, not the departing member's

## A household is a closed boundary

- A person who is not a member of a household cannot see or change anything inside it
- A person can be a member of any number of households at the same time
