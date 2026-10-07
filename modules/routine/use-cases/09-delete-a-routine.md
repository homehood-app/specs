---
status: draft
updated: 2026-10-07
superseded-by:
---

# Delete a routine

As the owner, an organizer, or the member who set it, I want to remove a routine that never ran so that a mistake does not stay on the record as history.

**Actors:** [[users#owner]], [[users#organizer]], [[users#member]], [[users#minor-member]]

## Pre-conditions

- The routine exists and has made no occurrence
- The actor is the owner, an organizer, or the member who created the routine for themselves

## Main flow

1. The actor deletes the routine.
2. The system removes it, with its schedule, its executor or rotation, and its record of misses.
3. Nothing is left. The routine never made an occurrence, so there is nothing to keep.

## Alternative flows

### The routine made at least one occurrence

1. It cannot be deleted. It is ended instead, and kept. See [[08-end-a-routine]].
2. This is the same line [[tasks/rules#archiving-ends-a-task-that-was-started]] draws for a task.

### The routine was set up for a start date in the future

1. It has made no occurrence yet, so it is deleted.

## Exception flows

### The routine has made an occurrence

1. The system refuses and says a routine that ran is ended, not deleted.
2. Nothing changes.

### The executor of somebody else's routine tries to delete it

1. The system refuses and says the routine belongs to whoever set it.
2. Nothing changes.

### An organizer deletes a routine whose executor is the owner

1. The system refuses and says an organizer cannot act on the owner's work.
2. Nothing changes.

## Post-conditions

- The routine does not exist
- No occurrence was removed, because there was none
- Nothing was lost that recorded something the household did

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every routine in the household | Delete any routine in the household that made no occurrence |
| Organizer | Every routine in the household | Delete any routine that made no occurrence and whose executor is not the owner |
| Member | The routines that concern them | Delete a routine they created for themselves that made no occurrence |
| Minor member | The routines that concern them | Delete a routine they created for themselves that made no occurrence |

## Applied business rules

- [[rules#pausing-keeps-a-routine-ending-stops-it-for-good]] — a routine that ran is ended, one that never ran is deleted
- [[rules#a-member-sets-a-routine-for-themselves-naming-another-member-needs-authority]] — who may delete what
- [[rules#an-organizer-cannot-act-on-the-owners-routines]] — authority stops at the owner
