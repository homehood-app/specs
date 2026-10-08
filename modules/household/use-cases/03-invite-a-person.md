---
status: draft
updated: 2026-10-08
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

### The person holds a minor account

1. The invitation is made the same way. A child can be invited into a home like anybody else — a child of separated parents is invited into the second one.
2. The system delivers it to the minor's guardian, not to the child, because the guardian is who answers it. See [[05-answer-an-invitation]].
3. The actor sees who the guardian is. You cannot invite a child into your home without knowing which person agreed to it.
4. How the actor identifies a minor account, which holds no email address of its own, is not specified yet — see [[accounts/overview]].

### The household wants to add a child who has no account yet

1. There is nothing to invite. Somebody makes the child a minor account first, and becomes its guardian.
2. How a minor account is created is not specified yet — see [[accounts/overview]].

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

### The invited minor's guardian is the actor

1. Nothing is refused. A parent who runs a household and invites their own child into it is the ordinary case, and the parent answers their own invitation.
2. The system still creates the invitation and still records the answer. A membership always has an invitation behind it.

## Post-conditions

- An invitation to this household exists in state `Pending`
- The invited person is not yet a member
- An invitation to a minor account is waiting on its guardian. An invitation to a full account is waiting on its holder

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every invitation to the household, its state, and the guardian of any minor invited | Invite any person, whatever kind of account they hold |
| Organizer | Every invitation to the household, its state, and the guardian of any minor invited | Invite any person, whatever kind of account they hold |
| Member | Nothing of this use case | Nothing |
| Minor | Nothing of this use case. A minor neither invites nor is told they were invited | Nothing |
| Guardian | An invitation addressed to a minor they hold | Nothing here. Answering it is [[05-answer-an-invitation]] |

## Applied business rules

- [[rules#the-owner-and-the-organizers-decide-who-belongs]] — a plain member cannot invite
- [[rules#membership-starts-with-an-accepted-invitation]] — an invitation is the one door in, for every kind of account
- [[rules#a-minors-memberships-are-their-guardians-to-decide]] — a minor can be invited anywhere, and the guardian is who answers
