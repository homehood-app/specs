# Household — Business Rules

## Authority over members runs owner, organizer, member

- The owner can act on any member
- An organizer can act on any member who is neither the owner nor another organizer
- A member can act on nobody but themselves
- A minor holds the member role, so a minor can act on nobody — and cannot act on themselves either, because a minor cannot leave

**Organizer authority** is the shorthand for "an organizer or the owner". The owner does everything an organizer does, so a household always has at least one member with organizer authority.

This rule is about acting on *people*. Asking another member for work is not acting on them — see [[tasks/rules#any-member-can-request-work-from-any-member]].

## A minor is a member and stays a member

Minor is what the account is, not what the person may do. See [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].

- A minor holds the member role, from the moment the account exists
- A minor cannot be promoted to organizer
- A minor cannot receive ownership of the household, and cannot create one
- A minor's role never changes, at any age. There is no path from a minor account to a full account — see [[decisions/0007-no-age-and-no-conversion-of-a-minor-account]]
- Apart from the bullets above, this module makes no distinction: everything a member sees, a minor sees, and everything a member may do, a minor may do

## A minor belongs to one household and cannot leave it

- A minor belongs to exactly one household
- A minor cannot be a member of a second household, and cannot be invited to one
- A minor cannot leave. Only a member with organizer authority takes them out — see [[use-cases/08-remove-a-member]]
- A minor account cannot exist outside a household. When the household removes a minor, or the household is deleted, the account ends with the membership
- The record of what a minor did stays whole. **A former member stays on what they left behind** holds for a minor like anybody else

## Only the owner changes the household itself

- Only the owner edits the household data
- Only the owner changes a member's role
- Only the owner hands ownership to another member
- Only the owner deletes the household

## The owner and the organizers decide who belongs

- A member with organizer authority can invite a person
- A member with organizer authority can revoke a pending invitation
- An organizer cannot remove the owner, and cannot remove another organizer

## Membership starts with an accepted invitation, or with a minor the household creates

There are two doors in, and no others.

- A person with an account of their own becomes a member by accepting an invitation
- A person is not a member while their invitation is `Pending`
- A person is not a member if their invitation is `Declined` or `Revoked`
- A child becomes a member when a member with organizer authority creates a minor account for them inside the household. There is no invitation and nothing to accept
- How a minor account is created, and how a child signs in to it, is not specified yet

## A household has exactly one owner, always

- The owner cannot leave or be removed while they are the owner
- To leave, the owner hands ownership to another member first, or deletes the household

## A former member stays on what they left behind

Leaving a household does not rewrite the past.

- A task keeps its requester and its executor after one of them leaves. A closed or archived task is a record of what happened, and it stays whole
- A comment keeps its author after they leave
- A former member sees none of it. They are outside the boundary

## An active task of a former member waits for organizer authority

- An `Open` or `Started` task whose requester or executor is a former member is **unresolved**
- An unresolved task is not lost, and is not silently handed to somebody else. It waits
- Only a member with organizer authority resolves it — see [[tasks/use-cases/08-resolve-a-former-members-tasks]]
- A member who leaves on their own does not resolve their own tasks. Redistributing the household's work is the household's call
- A member with organizer authority who removes somebody may resolve their tasks in the same step, or leave them unresolved

## A household is a closed boundary

- A person who is not a member of a household cannot see or change anything inside it
- A person with an account of their own can be a member of any number of households at the same time
- A minor is the exception: one household, and never a second
