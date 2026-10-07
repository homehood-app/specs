---
status: draft
updated: 2026-10-07
superseded-by:
---

# Invite a person

As the owner or an organizer, I want to invite a person so that they can join the household.

**Actors:** [[users#owner]], [[users#organizer]]

## Pre-conditions

- The household exists
- The actor is its owner or one of its organizers

## Main flow

1. The actor identifies the person to invite.
2. The system creates an invitation in state `Pending`.
3. The system delivers the invitation to the person.

## Alternative flows

### The household wants to add a child

1. A child is not invited. A member with organizer authority creates a minor account for them inside the household, and the child is a member from that moment.
2. There is nothing to deliver and nothing to accept. How a minor account is created is not specified yet — see [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].

### The person is already a member

1. The system refuses and says the person already belongs to the household.
2. No invitation is created.

### The person already has a pending invitation to this household

1. The system refuses and says an invitation is already waiting.
2. No second invitation is created.

### The person was invited before and declined, or the invitation was revoked

1. The system creates a new invitation. A final invitation does not block a new one.

## Exception flows

### Delivery fails

1. The invitation stays `Pending`.
2. The system tells the actor that it could not be delivered.

### The person holds a minor account

1. The system refuses and says a minor belongs to one household and cannot be invited to another.
2. No invitation is created. A minor account holds no address an invitation could reach.

## Post-conditions

- An invitation to this household exists in state `Pending`
- The invited person is not yet a member
- The invited person holds a full account. A minor is never the target of an invitation

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every invitation to the household, and its state | Invite any person who holds a full account |
| Organizer | Every invitation to the household, and its state | Invite any person who holds a full account |
| Member | Nothing of this use case | Nothing |
| Minor | Nothing of this use case | Nothing |

## Applied business rules

- [[rules#the-owner-and-the-organizers-decide-who-belongs]] — a plain member cannot invite
- [[rules#membership-starts-with-an-accepted-invitation-or-with-a-minor-the-household-creates]] — an invitation is one of the two doors in, and the only one for a person with their own account
- [[rules#a-minor-belongs-to-one-household-and-cannot-leave-it]] — a minor cannot be invited anywhere
