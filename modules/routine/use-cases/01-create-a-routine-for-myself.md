---
status: draft
updated: 2026-10-07
superseded-by:
---

# Create a routine for myself

As a member, I want to say that a piece of my work comes back so that I do not write the same task every morning.

**Actors:** [[users#member]], [[users#organizer]], [[users#owner]], [[users#minor-member]]

## Pre-conditions

- The actor is a member of the household

## Main flow

1. The member writes what the work is.
2. The member chooses the schedule: every day, every *n* days, chosen days of the week, or a date each month.
3. The member chooses the start date.
4. The system creates the routine in state `Active`, inside that household, with the member as its requester and as its only executor.
5. On the start date, the routine makes its first occurrence.

## Alternative flows

### The start date is today

1. The routine makes its first occurrence at once.

### The start date is a day the schedule does not give

1. The routine makes its first occurrence on the first date on or after the start date that the schedule gives.

## Exception flows

### The member names another member as the executor

1. The system refuses and says only the owner and an organizer can set a routine for somebody else.
2. No routine is created. See [[02-create-a-routine-for-another-member]].

### The routine has no description

1. The system refuses and asks what the work is.
2. No routine is created.

### No schedule is chosen

1. The system refuses and asks how often the work comes round.
2. No routine is created. A routine with no schedule would make nothing.

## Post-conditions

- The routine exists in state `Active`, with exactly one executor, who is also its requester
- The routine will make one occurrence for every date its schedule gives
- The member, the owner and every organizer can see the routine

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every routine in the household | Create a routine for themselves |
| Organizer | Every routine in the household | Create a routine for themselves |
| Member | The routines where they are the requester, the executor, or in the rotation | Create a routine for themselves, and for nobody else |
| Minor member | The routines where they are the requester, the executor, or in the rotation | Create a routine for themselves, and for nobody else |

## Applied business rules

- [[rules#a-member-sets-a-routine-for-themselves-naming-another-member-needs-authority]] — a routine for oneself is open to every role, a minor included
- [[rules#a-routine-makes-tasks-and-is-never-one]] — what the routine holds, and what it makes
- [[rules#an-occurrence-appears-on-its-due-date]] — when the first occurrence and every later one appears
- [[rules#a-routine-is-visible-to-the-people-its-occurrences-are-visible-to]] — who can see it from now on
