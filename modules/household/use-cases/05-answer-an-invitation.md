---
status: draft
updated: 2026-10-07
superseded-by:
---

# Answer an invitation

As an invited person, I want to accept or decline so that I join the household or stay out of it.

**Actors:** [[users#member]]

## Pre-conditions

- An invitation to the person exists in state `Pending`
- The person holds a full account. A minor is never invited

## Main flow

1. The person opens the invitation.
2. The person accepts it.
3. The system sets the invitation to `Accepted`.
4. The system makes the person a member of the household, with the plain member role.

## Alternative flows

### The person declines

1. The system sets the invitation to `Declined`.
2. The person does not become a member.
3. The household sees the answer.

### The person already belongs to other households

1. The system adds this membership to the others. Nothing is replaced.

## Exception flows

### The invitation is no longer pending

1. The system refuses and says the invitation is already answered or was revoked.
2. Nothing changes.

### The household no longer exists

1. The system refuses and says the household is gone.
2. Nothing changes.

## Post-conditions

- The invitation is `Accepted` or `Declined`, and cannot be answered again
- On accept, the person is a member of the household, with the plain member role

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | The answer to any invitation to the household | Nothing. Nobody can answer for the invited person |
| Organizer | The answer to any invitation to the household | Nothing |
| Member | Their own pending invitation | Accept it or decline it |
| Minor | Nothing of this use case. A minor arrives by the household creating their account, not by an invitation | Nothing |

## Applied business rules

- [[rules#membership-starts-with-an-accepted-invitation-or-with-a-minor-the-household-creates]] — accepting is what makes a person with their own account a member; a minor comes in by the other door
