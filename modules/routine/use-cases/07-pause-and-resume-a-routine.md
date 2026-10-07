---
status: draft
updated: 2026-10-07
superseded-by:
---

# Pause and resume a routine

As the owner, an organizer, or the member who set it, I want to stop a routine for a while so that a holiday does not fill the household's record with misses.

**Actors:** [[users#owner]], [[users#organizer]], [[users#member]], [[users#minor-member]]

## Pre-conditions

- The routine exists
- The actor is the owner, an organizer, or the member who created the routine for themselves

## Main flow

1. The actor pauses the routine.
2. The system sets it to `Paused`. It makes no further occurrence.
3. The system records no miss for any date while the routine is paused. Nothing was missed, because nothing was asked for.
4. Later, the actor makes the routine active again.
5. The system sets it to `Active`, and it makes its next occurrence on the first date its schedule gives from that day.

## Alternative flows

### The routine has an occurrence waiting when it is paused

1. The waiting occurrence stays as it is. It was already asked for.
2. Its executor does it, or somebody deletes it. Pausing the routine does not decide that.

### The routine has a rotation

1. The turn is kept exactly where it was.
2. The first occurrence after the pause goes to the member whose turn it was.

### The routine is paused because a member left

1. The system paused it, not a member. See [[10-resolve-a-routine-of-a-former-member]].
2. It cannot be made active again until it names only current members.

## Exception flows

### The routine is `Ended`

1. The system refuses and says an ended routine does not become active again.
2. Nothing changes. `Ended` is final — see [[08-end-a-routine]].

### Somebody expects the skipped dates to appear

1. They do not. A resumed routine starts from today and never makes an occurrence for a date in the past.
2. If the work from those dates still needs doing, somebody creates an ordinary task for it.

### The executor of somebody else's routine tries to pause it

1. The system refuses and says the routine belongs to whoever set it.
2. Nothing changes.

### An organizer pauses a routine whose executor is the owner

1. The system refuses and says an organizer cannot act on the owner's work.
2. Nothing changes.

## Post-conditions

- The routine is `Paused` and makes no occurrence, or `Active` and makes them again from today
- No miss was recorded for any date in the pause
- The turn of a rotation is where it was before the pause
- The routine keeps its description, its schedule, its people and its record

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every routine in the household, and which are paused | Pause and resume any routine in the household |
| Organizer | Every routine in the household, and which are paused | Pause and resume any routine whose executor is not the owner |
| Member | The routines that concern them, and which are paused | Pause and resume a routine they created for themselves |
| Minor member | The routines that concern them, and which are paused | Pause and resume a routine they created for themselves |

## Applied business rules

- [[rules#pausing-keeps-a-routine-ending-stops-it-for-good]] — what a pause keeps, and what a resume does not make up
- [[rules#an-occurrence-appears-on-its-due-date]] — a paused routine makes none
- [[rules#a-member-sets-a-routine-for-themselves-naming-another-member-needs-authority]] — who may pause what
- [[rules#a-routine-with-a-former-member-on-it-pauses]] — the one pause nobody chose
