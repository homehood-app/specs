---
status: draft
updated: 2026-10-06
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
2. The owner sets their role to organizer or to member.
3. The system applies the new role at once.

## Alternative flows

### A member is promoted to organizer

1. They gain authority over members and over the work of members, immediately.
2. They cannot act on the owner, and cannot remove another organizer.

### An organizer is demoted to member

1. They lose sight of the household's other work at once, keeping only what concerns them.
2. The tasks where they are the requester or the executor are untouched.

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
| Owner | Every member and their role | Promote any member to organizer, or demote any organizer to member |
| Organizer | Every member and their role | Nothing. An organizer cannot make or unmake a peer |
| Member | Their own role | Nothing |
| Minor member | Their own role | Nothing |

## Applied business rules

- [[rules#only-the-owner-changes-the-household-itself]] — a role change is the owner's alone
- [[rules#authority-over-members-runs-owner-organizer-member]] — what the new role can do
