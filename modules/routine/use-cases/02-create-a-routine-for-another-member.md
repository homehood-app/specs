---
status: draft
updated: 2026-10-07
superseded-by:
---

# Create a routine for another member

As the owner or an organizer, I want to give a member standing work so that the household's routine is set once and not asked for every day.

**Actors:** [[users#owner]], [[users#organizer]]

## Pre-conditions

- The actor is the owner or an organizer of the household
- The chosen executor is a member of the household

## Main flow

1. The owner or organizer writes what the work is.
2. They choose the schedule and the start date.
3. They choose the executor: a member of the household.
4. The system creates the routine in state `Active`, with themselves as its requester and the chosen member as its executor.
5. On the start date, the routine makes its first occurrence, with the chosen member as its executor.
6. The executor, the requester, the owner and every organizer see the routine and its occurrences from now on.

## Alternative flows

### The work is shared between members

1. They set a rotation instead of a single executor. See [[03-set-a-rotation-on-a-routine]].

## Exception flows

### The actor is a member or a minor member

1. The system refuses and says only the owner and an organizer can set a routine for somebody else.
2. No routine is created. The member can set a routine for themselves — see [[01-create-a-routine-for-myself]].

### An organizer chooses the owner as the executor

1. The system refuses and says an organizer cannot act on the owner's work.
2. No routine is created. The owner sets their own routines.

### The chosen executor is not a member of the household

1. The system refuses and says the person is not in this household.
2. No routine is created.

## Post-conditions

- The routine exists in state `Active`, with one requester and one executor, who are two different members
- The executor cannot change, pause or end the routine. They do each occurrence
- The requester, the executor, the owner and every organizer can see the routine

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every routine in the household | Create a routine for any member |
| Organizer | Every routine in the household | Create a routine for any member who is not the owner |
| Member | The routines where they are the requester, the executor, or in the rotation | Nothing. A member cannot set a routine for somebody else |
| Minor member | The routines where they are the requester, the executor, or in the rotation | Nothing. A minor cannot set a routine for somebody else |

## Applied business rules

- [[rules#a-member-sets-a-routine-for-themselves-naming-another-member-needs-authority]] — naming another member needs organizer authority
- [[rules#an-organizer-cannot-act-on-the-owners-routines]] — authority over a member's routine stops at the owner
- [[rules#the-executor-of-an-occurrence-is-whoevers-turn-it-is]] — every occurrence goes to the named executor
- [[rules#a-routine-is-visible-to-the-people-its-occurrences-are-visible-to]] — the requester keeps sight of work they asked for
