---
status: draft
updated: 2026-10-07
superseded-by:
---

# Create a household

As a person, I want to create a household so that I can start coordinating a home's routine.

**Actors:** [[users#owner]]

## Pre-conditions

- The person holds a full account

## Main flow

1. The person gives the household a name.
2. The system creates the household.
3. The system makes the person a member of it, and its owner.

## Alternative flows

None. A person who already belongs to one or more households creates another the same way, and belongs to all of them.

## Exception flows

### The name is empty

1. The system refuses and asks for a name.
2. No household is created.

### The person holds a minor account

1. The system refuses. A minor cannot hold the owner role, and creating a household makes you its owner.
2. No household is created. A minor joins a household when their guardian accepts an invitation for them — see [[05-answer-an-invitation]].

## Post-conditions

- The household exists
- The person is its only member, and its owner
- The household has no tasks

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | The household they just created, empty | Create a household, and become its owner |
| Organizer | Nothing of this use case. There is no household yet to be an organizer of | Nothing |
| Member | Nothing of this use case | Create another household, and become its owner |
| Minor | Nothing of this use case | Nothing. A minor cannot create a household |

## Applied business rules

- [[rules#a-household-has-exactly-one-owner-always]] — the creator becomes the owner, so the rule holds from the first moment
- [[rules#a-household-is-a-closed-boundary]] — belonging to one household never blocks belonging to another, for anybody
- [[rules#a-minor-is-a-member-and-stays-a-member]] — a minor cannot hold the owner role, so a minor cannot start a household
