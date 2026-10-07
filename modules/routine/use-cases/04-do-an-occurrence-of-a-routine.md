---
status: draft
updated: 2026-10-07
superseded-by:
---

# Do an occurrence of a routine

As the executor of an occurrence, I want to do today's turn of a routine so that the work is done and the record shows I did it.

**Actors:** [[users#member]], [[users#organizer]], [[users#owner]], [[users#minor-member]]

## Pre-conditions

- A routine made an occurrence, and the actor is its executor

## Main flow

1. The executor sees the occurrence in their work, next to their other tasks.
2. The occurrence says which routine it came from and which date it is for.
3. The executor starts it. See [[tasks/use-cases/03-start-a-task]].
4. The executor closes it. See [[tasks/use-cases/05-close-a-task]].
5. The routine is untouched. It makes the next occurrence on the next date its schedule gives.

## Alternative flows

### The work is no longer needed today

1. The occurrence is archived if it was started, or deleted if it was not. See [[tasks/use-cases/06-archive-a-task]] and [[tasks/use-cases/07-delete-a-task]].
2. The routine is untouched and records no miss. Somebody decided, so nothing was missed.

### The occurrence is commented on

1. Comments belong to the occurrence, not to the routine. See [[tasks/use-cases/04-comment-on-a-task]].
2. Tuesday's comment stays on Tuesday's occurrence.

## Exception flows

### The executor tries to close the routine

1. There is nothing to close. A routine is never started and never closed, only the occurrence is.
2. Nothing changes.

### The executor tries to do tomorrow's occurrence today

1. There is nothing to do. An occurrence does not exist before its due date.
2. Nothing changes.

### The executor does not want this routine at all

1. They cannot change or end a routine somebody else created. They ask the owner or an organizer.
2. Nothing changes. See [[06-edit-a-routine]] and [[08-end-a-routine]].

## Post-conditions

- The occurrence is in `Closed`, which is final, and it is a record of one date
- Earlier occurrences of the same routine are untouched. Every date has its own record
- The routine is unchanged, and still `Active`

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every occurrence in the household, and which routine each came from | Start and close an occurrence only when they are its executor |
| Organizer | Every occurrence in the household, and which routine each came from | Start and close an occurrence only when they are its executor |
| Member | The occurrences where they are the requester or the executor, and which routine each came from | Start and close an occurrence they are the executor of |
| Minor member | The occurrences where they are the requester or the executor, and which routine each came from | Start and close an occurrence they are the executor of |

## Applied business rules

- [[rules#a-routine-makes-tasks-and-is-never-one]] — the occurrence is the work, and closing it does nothing to the routine
- [[tasks/rules#the-executor-works-the-task]] — nobody does another member's occurrence
- [[tasks/rules#a-task-moves-in-one-direction]] — an occurrence is begun before it is finished, and `Closed` is final
- [[rules#a-routine-is-visible-to-the-people-its-occurrences-are-visible-to]] — a member in a rotation sees only the occurrences that fell to them
