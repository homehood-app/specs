---
status: draft
updated: 2026-10-07
superseded-by:
---

# Edit a routine

As the owner, an organizer, or the member who set it, I want to change a routine so that it matches how the household actually works.

**Actors:** [[users#owner]], [[users#organizer]], [[users#member]], [[users#minor-member]]

## Pre-conditions

- The routine exists and is `Active` or `Paused`
- The actor is the owner, an organizer, or the member who created the routine for themselves

## Main flow

1. The actor changes what the work is, the schedule, or the executor.
2. The system saves the routine.
3. The change applies to every occurrence the routine makes from now on.
4. Occurrences that already exist are untouched.

## Alternative flows

### The schedule changes

1. The next occurrence appears on the first date the new schedule gives, on or after today.
2. A waiting occurrence from the old schedule stays waiting until it is done, or until the next occurrence replaces it — see [[05-miss-an-occurrence]].

### The executor changes

1. Occurrences that already exist keep the executor they were made with. Nobody is given work they were not asked for, and nobody loses credit for work they did.
2. The next occurrence goes to the new executor.
3. Changing a single executor to a rotation, or back, is [[03-set-a-rotation-on-a-routine]].

### The member changes their own routine

1. A member can change every part of a routine they created for themselves, as long as they stay its only executor.

## Exception flows

### A member changes the executor of their own routine to somebody else

1. The system refuses and says only the owner and an organizer can set a routine for another member.
2. Nothing changes.

### The executor of somebody else's routine tries to change it

1. The system refuses and says the routine belongs to whoever set it.
2. Nothing changes. They do each occurrence, and they ask the owner or an organizer for a change.

### An organizer changes a routine whose executor is the owner

1. The system refuses and says an organizer cannot act on the owner's work.
2. Nothing changes.

### The routine is `Ended`

1. The system refuses and says an ended routine does not change.
2. Nothing changes. The household writes a new routine.

## Post-conditions

- The routine holds the new description, schedule or executor
- Every occurrence that already exists is unchanged, including the one waiting
- The routine's state is the state it was in before the change

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every routine in the household | Change any routine in the household |
| Organizer | Every routine in the household | Change any routine whose executor is not the owner |
| Member | The routines that concern them | Change a routine they created for themselves, and keep themselves as its executor |
| Minor member | The routines that concern them | Change a routine they created for themselves, and keep themselves as its executor |

## Applied business rules

- [[rules#a-member-sets-a-routine-for-themselves-naming-another-member-needs-authority]] — who may change what
- [[rules#an-organizer-cannot-act-on-the-owners-routines]] — authority stops at the owner
- [[rules#an-occurrence-appears-on-its-due-date]] — when the new schedule takes effect
- [[rules#a-routine-makes-tasks-and-is-never-one]] — editing the routine does not edit the tasks it already made
