---
status: draft
updated: 2026-10-06
superseded-by:
---

# Revoke an invitation

As the owner or an organizer, I want to withdraw an invitation so that somebody we no longer want to invite cannot walk in later.

**Actors:** [[users#owner]], [[users#organizer]]

## Pre-conditions

- An invitation to the household exists in state `Pending`
- The actor is the household's owner or one of its organizers

## Main flow

1. The actor selects the pending invitation.
2. The actor revokes it.
3. The system sets the invitation to `Revoked`.
4. The invited person can no longer answer it.

## Alternative flows

### Another organizer sent the invitation

1. The actor revokes it anyway. An invitation belongs to the household, not to the person who sent it.

## Exception flows

### The invitation is no longer pending

1. The system refuses and says the invitation is already answered or already revoked.
2. Nothing changes.

### The actor is a plain member

1. The system refuses.
2. Nothing changes.

## Post-conditions

- The invitation is `Revoked` and cannot be answered
- The invited person is not a member
- The same person can be invited again later

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every invitation to the household | Revoke any pending invitation |
| Organizer | Every invitation to the household | Revoke any pending invitation, including one another organizer sent |
| Member | Nothing of this use case | Nothing |
| Minor member | Nothing of this use case | Nothing |

## Applied business rules

- [[rules#the-owner-and-the-organizers-decide-who-belongs]] — revoking is part of deciding who belongs
