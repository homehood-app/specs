# Household — Business Rules

## Authority over members runs owner, organizer, member, minor

- The owner can act on any member
- An organizer can act on any member who is neither the owner nor another organizer
- A member can act on nobody but themselves
- A minor can act on nobody, not even themselves. A minor cannot end their own membership

**Organizer authority** is the shorthand for "an organizer or the owner". The owner does everything an organizer does, so a household always has at least one member with organizer authority.

This rule is about acting on *people*. Asking another member for work is not acting on them — see [[tasks/rules#any-member-can-request-work-from-any-member]].

## A minor does not see who runs the household

A minor sees the people of the household. A minor does not see the ladder they stand on. See [[decisions/0006-a-minor-is-reduced-on-the-household-not-on-the-work]].

- A minor sees every member of the household by name
- A minor does not see which member is the owner
- A minor does not see which members are organizers
- A minor sees their own role, and no other member's role
- Where a minor chooses a member — naming the executor of a task, for example — they are shown names, not roles
- Everything the household already keeps from a plain member stays hidden from a minor as well: invitations, role changes and removals

This hides the information, not the people. A minor still sees who asked for a task and who will do it, because that is the work and not the household — see [[tasks/rules#a-minor-sees-their-own-work-in-full]].

## Only the owner changes the household itself

- Only the owner edits the household data
- Only the owner changes a member's role
- Only the owner hands ownership to another member
- Only the owner deletes the household

## The owner and the organizers decide who belongs

- A member with organizer authority can invite a person
- A member with organizer authority can revoke a pending invitation
- An organizer cannot remove the owner, and cannot remove another organizer

## Membership starts with an accepted invitation

There is no other way into a household.

- A person is not a member while their invitation is `Pending`
- A person is not a member if their invitation is `Declined` or `Revoked`

## A household has exactly one owner, always

- The owner cannot leave or be removed while they are the owner
- To leave, the owner hands ownership to another member first, or deletes the household

## A minor cannot take themselves out of a household

Leaving a home is not a child's act. See [[decisions/0006-a-minor-is-reduced-on-the-household-not-on-the-work]].

- A member and an organizer each end their own membership, whenever they want — see [[use-cases/09-leave-a-household]]
- A minor cannot. A member with organizer authority removes them — see [[use-cases/08-remove-a-member]]
- Removal is the only way a minor leaves a household, and it carries the same decision about their active tasks as any other removal
- A minor who becomes a plain member can leave on their own from that moment

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
- A person can be a member of any number of households at the same time
