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
- The person holds a full account. A minor's role never changes while the account is a minor account

## Main flow

1. The owner selects a member.
2. The owner sets their role to organizer or to member.
3. The system applies the new role at once.

## Alternative flows

### A member is promoted to organizer

1. They gain authority over members and over the work of members, immediately.
2. They cannot act on the owner, and cannot remove another organizer.

### An organizer is demoted to member

1. They lose sight of the household's other work at once, keeping only what concerns them.
2. The tasks where they are the requester or the executor are untouched.

### The household wants to give a child more

1. A minor's role cannot change while the account is a minor account, and the household cannot change that. The owner of a household does not decide when somebody else's child grows up.
2. The child's guardian makes the account a full account. See [[accounts/use-cases/04-make-a-minor-account-a-full-account]]. The person keeps this membership and everything they did in it — nobody is removed and re-invited.
3. They are then a plain member holding a full account, and this use case can promote them like anybody else.

## Exception flows

### The actor is an organizer, not the owner

1. The system refuses and says only the owner changes a role.
2. Nothing changes.

### The target is the owner

1. The system refuses and says the owner's role is changed by handing ownership on. See [[07-transfer-ownership]].
2. Nothing changes.

### The target holds a minor account

1. The system refuses and says a minor is always a member.
2. Nothing changes. A minor is never promoted, and the household has no way to make one eligible. Only the child's guardian changes what the account is — see [[accounts/rules#a-minor-account-becomes-a-full-account-once]].

## Post-conditions

- The member holds the new role
- The household still has exactly one owner
- No task changed its requester or its executor

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every member and their role | Promote any member with a full account to organizer, or demote any organizer to member |
| Organizer | Every member and their role | Nothing. An organizer cannot make or unmake a peer |
| Member | Their own role | Nothing |
| Minor | Their own role | Nothing. A minor's role never changes while the account is a minor account |
| Guardian | Nothing of this use case | Nothing. A guardian cannot give the child a role, or take one away |

## Applied business rules

- [[rules#only-the-owner-changes-the-household-itself]] — a role change is the owner's alone
- [[rules#authority-over-members-runs-owner-organizer-member]] — what the new role can do
- [[rules#a-minor-is-a-member-and-stays-a-member]] — a minor is never promoted while the account is a minor account
- [[accounts/rules#a-guardian-decides-the-account-not-the-household]] — the guardian changes the kind of account, and never the role
