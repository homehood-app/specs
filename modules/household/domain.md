# Household — Domain

Concepts specific to this module. The household, member, owner, organizer, minor and invitation themselves are defined in the shared [[domain]].

## Invitation state

An invitation is in exactly one state at a time:

| State | Meaning |
| --- | --- |
| Pending | Sent, and waiting for an answer |
| Accepted | Answered yes. The person is now a member |
| Declined | Answered no. The person is not a member |
| Revoked | Withdrawn by the household before it was answered |

Only a `Pending` invitation can be answered or revoked. The other three states are final.

## Household data

What the household holds about itself, apart from its members and their work: its name, and anything else that describes the home rather than the people in it.

Only the owner changes it.
