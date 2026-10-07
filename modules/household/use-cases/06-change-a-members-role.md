---
status: draft
updated: 2026-10-07
superseded-by:
---

# Change a member's role

As the owner, I want to promote or demote a member so that the people who run the household are the right ones.

**Actors:** [[users#owner]]

## Pre-conditions

- The household exists
- The actor is its owner
- The person is a member of it, and is not the owner

## Main flow

1. The owner selects a member.
2. The owner sets their role: organizer, member or minor.
3. The system applies the new role at once.

## Alternative flows

### A member is promoted to organizer

1. They gain authority over members and over the work of members, immediately.
2. They cannot act on the owner, and cannot remove another organizer.

### An organizer is demoted to member

1. They lose sight of the household's other work at once, keeping only what concerns them.
2. The tasks where they are the requester or the executor are untouched.

### A minor becomes a plain member

1. This is how a child who has grown up gets the rest of the product. There is no other mechanism, and nothing happens by age — see [[decisions/0007-one-minor-role-at-every-age]].
2. They now see who the owner is and which members are organizers, and they can leave the household on their own.
3. Their tasks are untouched. Nothing about their own work changes, because a minor already had a member's authority over it.

### A plain member becomes a minor

1. The reverse of the same act. They stop seeing who runs the household, and can no longer leave on their own.
2. Their tasks are untouched.

### A minor is made an organizer

1. They are an organizer, and are not a minor any more. There is no minor organizer and no minor owner — see [[decisions/0004-four-roles-owner-organizer-member-minor]].
2. The owner is choosing to say this person is no longer a child in the household. One act, one role.

## Exception flows

### The actor is an organizer, not the owner

1. The system refuses and says only the owner changes a role.
2. Nothing changes.

### The target is the owner

1. The system refuses and says the owner's role is changed by handing ownership on. See [[07-transfer-ownership]].
2. Nothing changes.

## Post-conditions

- The member holds the new role
- The household still has exactly one owner
- No task changed its requester or its executor

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every member and their role | Set any other member's role: organizer, member or minor |
| Organizer | Every member and their role | Nothing. An organizer cannot make or unmake a peer |
| Member | Their own role, and who the owner is | Nothing |
| Minor member | Their own role, and no other member's role | Nothing |

## Applied business rules

- [[rules#only-the-owner-changes-the-household-itself]] — a role change is the owner's alone
- [[rules#authority-over-members-runs-owner-organizer-member-minor]] — what the new role can do
- [[rules#a-minor-does-not-see-who-runs-the-household]] — a minor sees their own role and nobody else's, so a promotion elsewhere is invisible to them
