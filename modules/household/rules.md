# Household — Business Rules

## Authority over members runs owner, organizer, member

- The owner can act on any member
- An organizer can act on any member who is neither the owner nor another organizer
- A member can act on nobody but themselves
- A minor holds the member role, so a minor can act on nobody — and cannot act on themselves either, because a minor cannot leave. Their guardian acts on their membership instead, and on nothing else in the household

**Organizer authority** is the shorthand for "an organizer or the owner". The owner does everything an organizer does, so a household always has at least one member with organizer authority.

This rule is about acting on *people*. Asking another member for work is not acting on them — see [[tasks/rules#any-member-can-request-work-from-any-member]].

## A minor is a member and stays a member

Minor is what the account is, not what the person may do. See [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].

- A minor holds the member role in every household they belong to
- A minor cannot be promoted to organizer
- A minor cannot receive ownership of the household, and cannot create one
- A minor's role never changes while the account is a minor account, and nothing about it depends on an age. A minor account becomes a full account only by its guardian's decision, outside this module — see [[accounts/rules#a-minor-account-becomes-a-full-account-once]]
- Apart from the bullets above, this module makes no distinction: everything a member sees, a minor sees, and everything a member may do, a minor may do

## A minor's memberships are their guardian's to decide

A minor belongs where their guardian puts them, and leaves when the household or the guardian says so. See [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].

- A minor can be a member of any number of households, like anybody else. A child of separated parents belongs to both homes
- A minor does not answer an invitation. Their guardian answers it for them — see [[use-cases/05-answer-an-invitation]]
- A minor cannot leave a household. Two people can take them out: a member with organizer authority in that household, and the minor's guardian — see [[use-cases/08-remove-a-member]]
- A minor account does not end when a membership does. It survives removal, and it survives the deletion of a household. Only its guardian ends it — see [[accounts/rules#only-the-guardian-ends-a-minor-account]]
- A minor account can belong to no household at all and still exist. Its guardian holds it
- A guardian who stops being a member of a household does not take their minor out of it. The two memberships are separate, and a guardian who wants the child out removes them
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

## Membership starts with an accepted invitation

One door in, for every kind of account.

- A person becomes a member by accepting an invitation to the household
- A full account is answered by its own holder. A minor account is answered by its guardian
- A person is not a member while their invitation is `Pending`
- A person is not a member if their invitation is `Declined` or `Revoked`
- **Making a minor account does not put it into a household.** There is no second door. A guardian who runs the household invites their own child and answers that invitation themselves — see [[accounts/use-cases/01-create-a-minor-account]]
- An invitation to a minor account is addressed to its guardian. A minor account cannot be addressed directly, because it holds no email address and its handle is not an address — see [[use-cases/03-invite-a-person]]

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
- A guardian who takes their minor out of a household never resolves anything. They cannot see the work, so it always waits for the household — see [[use-cases/08-remove-a-member]]

## A household is a closed boundary

- A person who is not a member of a household cannot see or change anything inside it
- Any account can be a member of any number of households at the same time. A minor is no exception
- A guardian is no exception either. A guardian who is not a member of a household sees nothing inside it, not even of the minor they hold: not their tasks, not the other members, not who the owner is. They see the household's name and that the minor is a member of it, because otherwise they could not tell one of the child's homes from another. Nothing more than that
- Taking a minor out of a household is not seeing into it. A guardian can remove their minor from a household they cannot see — see [[use-cases/08-remove-a-member]]
