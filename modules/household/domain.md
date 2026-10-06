# Household — Domain

Concepts specific to this module. The household, member, organizer, minor and invitation themselves are defined in the shared [[domain]].

## Invitation state

An invitation is in exactly one state at a time:

| State | Meaning |
| --- | --- |
| Pending | Sent, and waiting for an answer |
| Accepted | Answered yes. The person is now a member |
| Declined | Answered no. The person is not a member |

An invitation in any state other than `Pending` cannot be answered again.
