---
status: draft
updated: 2026-10-06
superseded-by:
---

# Invite a person

As an organizer, I want to invite a person so that they can join the household.

**Actors:** [[users#organizer]]

## Pre-conditions

- The household exists
- The actor is an organizer of it

## Main flow

1. The organizer identifies the person to invite.
2. The organizer says whether the person will be a minor member.
3. The system creates an invitation in state `Pending`.
4. The system delivers the invitation to the person.

## Alternative flows

### The person is already a member

1. The system refuses and says the person already belongs to the household.
2. No invitation is created.

### The person already has a pending invitation to this household

1. The system refuses and says an invitation is already waiting.
2. No second invitation is created.

## Exception flows

### Delivery fails

1. The invitation stays `Pending`.
2. The system tells the organizer that it could not be delivered.

## Post-conditions

- An invitation to this household exists in state `Pending`
- The invited person is not yet a member

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Organizer | The invitations they have sent, and their state | Invite a person, and set whether they will be a minor member |
| Member | Nothing of this use case | Nothing |
| Minor member | Nothing of this use case | Nothing |

## Applied business rules

- [[rules#only-an-organizer-changes-the-membership]] — a member who is not an organizer cannot invite
- [[rules#membership-starts-with-an-accepted-invitation]] — the invitation is the only door in
