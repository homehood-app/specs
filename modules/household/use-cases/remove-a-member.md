---
status: draft
updated: 2026-10-06
superseded-by:
---

# Remove a member

As an organizer, I want to remove a member so that the household matches who really lives here.

**Actors:** [[users#organizer]]

## Pre-conditions

- The household exists
- The actor is an organizer of it
- The person to remove is a member of it

## Main flow

1. The organizer selects the member to remove.
2. The system shows how many tasks that member owns.
3. The organizer confirms.
4. The system removes the member from the household.

## Alternative flows

### The member owns tasks

1. The organizer chooses another member to take the tasks over, or chooses to delete them.
2. The system applies the choice, then removes the member.

## Exception flows

### The member is the only organizer

1. The system refuses and says the household must keep an organizer.
2. Nothing changes.

### The organizer removes themselves while another organizer exists

1. The system removes them.
2. They lose access to the household.

## Post-conditions

- The person is no longer a member
- No task in the household is owned by a person who is not a member
- The household still has at least one organizer

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Organizer | Every member of the household, and how many tasks each one owns | Remove any member, including themselves while another organizer remains |
| Member | That they are no longer in the household | Nothing. A member cannot remove anybody, including themselves |
| Minor member | That they are no longer in the household | Nothing |

## Applied business rules

- [[rules#only-an-organizer-changes-the-membership]] — removal is the organizer's authority alone
- [[rules#a-household-always-has-an-organizer]] — the last organizer cannot be removed
- [[rules#a-household-is-a-closed-boundary]] — a removed person loses all access
