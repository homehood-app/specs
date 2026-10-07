---
status: draft
updated: 2026-10-07
superseded-by:
---

# Miss an occurrence

As the executor of a routine, I want yesterday's untouched turn to go away so that what I see today is what I can do today.

**Actors:** [[users#member]], [[users#organizer]], [[users#owner]], [[users#minor-member]]

## Pre-conditions

- A routine has an occurrence still in `Open`
- The routine reaches the due date of the next occurrence

## Main flow

1. The routine makes the new occurrence.
2. The system finds the earlier occurrence still in `Open`: nobody started it and nobody closed it.
3. The system deletes it.
4. The system records a miss on the routine, for that date.
5. The executor has one occurrence waiting: today's.

## Alternative flows

### The earlier occurrence was started

1. The system leaves it exactly as it is.
2. The routine records no miss. The work was begun, so it was not missed.
3. Its executor closes it when the work is done, or it is archived like any other started task.
4. The executor has today's occurrence as well. One is the work they began, the other is today's turn.

### The earlier occurrence was closed or archived

1. There is nothing waiting. The routine records no miss.

### The household was away for a week

1. Every date in the week records a miss, one for each occurrence the routine made and nobody did.
2. One occurrence is waiting at the end of it: today's.

## Exception flows

### The executor wants to do the missed date now

1. They cannot. The occurrence is gone, and a miss cannot be done, closed or undone.
2. The record keeps the miss. If the work still needs doing, somebody creates an ordinary task for it — see [[tasks/use-cases/01-create-a-task]].

### Somebody wants to remove a miss from the record

1. They cannot. A miss is a record of a date on which the work did not happen.
2. Deleting the routine removes its misses with it, because it removes the routine. See [[09-delete-a-routine]].

## Post-conditions

- Exactly one occurrence of the routine is in `Open`: the one for today
- The routine holds a miss for each date nobody did and nobody started
- No deleted occurrence had been started. Nothing anybody worked on was removed
- A miss is on the routine, never on a task, so it cannot be closed and cannot be counted as work

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every routine in the household and its misses, for any member | Nothing. The miss happens on its own, and nobody can add or remove one |
| Organizer | Every routine in the household and its misses, for any member | Nothing. The miss happens on its own, and nobody can add or remove one |
| Member | The misses of the routines that concern them | Nothing. They cannot do the missed date and cannot clear the miss |
| Minor member | The misses of the routines that concern them | Nothing. They cannot do the missed date and cannot clear the miss |

## Applied business rules

- [[rules#a-routine-never-has-two-occurrences-waiting]] — one open occurrence at a time, and what the miss is
- [[rules#an-occurrence-appears-on-its-due-date]] — the new occurrence appears whatever happened to the one before
- [[tasks/rules#archiving-ends-a-task-that-was-started]] — nothing started is deleted, nothing unstarted is kept
- [[tasks/rules#who-can-end-a-task]] — the routine deletes its own waiting occurrence
