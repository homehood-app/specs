---
status: draft
updated: 2026-10-07
superseded-by:
---

# End a routine

As the owner, an organizer, or the member who set it, I want to stop a routine for good so that the household stops being asked for work it does not want, without losing the record of what it did.

**Actors:** [[users#owner]], [[users#organizer]], [[users#member]], [[users#minor-member]]

## Pre-conditions

- The routine exists, is `Active` or `Paused`, and has made at least one occurrence
- The actor is the owner, an organizer, or the member who created the routine for themselves

## Main flow

1. The actor ends the routine.
2. The system sets it to `Ended`. It makes no further occurrence, ever.
3. The system deletes the occurrence waiting in `Open`, if there is one. It is work nobody wants any more.
4. Every other occurrence is untouched: closed ones stay closed, started ones stay started, and the misses stay on the record.

## Alternative flows

### The routine never made an occurrence

1. It is deleted, not ended. There is nothing in it worth keeping. See [[09-delete-a-routine]].

### An occurrence of the routine is `Started`

1. It stays as it is. Somebody began that work, and ending the routine does not take it off them.
2. Its executor closes it, or it is archived like any other started task.

### The household wants the routine back

1. It does not come back. `Ended` is final.
2. They create a new routine. See [[01-create-a-routine-for-myself]] and [[02-create-a-routine-for-another-member]].

## Exception flows

### The routine is already `Ended`

1. The system refuses.
2. Nothing changes.

### The executor of somebody else's routine tries to end it

1. The system refuses and says the routine belongs to whoever set it.
2. Nothing changes. They ask the owner or an organizer.

### An organizer ends a routine whose executor is the owner

1. The system refuses and says an organizer cannot act on the owner's work.
2. Nothing changes.

## Post-conditions

- The routine is `Ended`, which is final, and makes no occurrence
- No occurrence in `Open` is left over from it
- Every started, closed and archived occurrence it made is unchanged
- The routine's record is kept: what the work was, who did each turn, and every miss

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every routine in the household, and which are ended | End any routine in the household |
| Organizer | Every routine in the household, and which are ended | End any routine whose executor is not the owner |
| Member | The routines that concern them, and which are ended | End a routine they created for themselves |
| Minor member | The routines that concern them, and which are ended | End a routine they created for themselves |

## Applied business rules

- [[rules#pausing-keeps-a-routine-ending-stops-it-for-good]] — `Ended` is final, and what it does to the waiting occurrence
- [[rules#a-member-sets-a-routine-for-themselves-naming-another-member-needs-authority]] — who may end what
- [[rules#an-organizer-cannot-act-on-the-owners-routines]] — authority stops at the owner
- [[tasks/rules#archiving-ends-a-task-that-was-started]] — the waiting occurrence was never started, so it is deleted
