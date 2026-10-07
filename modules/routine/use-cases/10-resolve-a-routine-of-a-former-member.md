---
status: draft
updated: 2026-10-07
superseded-by:
---

# Resolve a routine of a former member

As the owner or an organizer, I want to decide what happens to a routine somebody left behind so that the household's routine carries on without work being handed to anybody by accident.

**Actors:** [[users#owner]], [[users#organizer]]

## Pre-conditions

- A member on a routine stopped being a member of the household
- The system paused the routine
- The actor is the owner or an organizer

## Main flow

1. The system paused the routine the moment the member stopped being a member. It makes no further occurrence.
2. The owner or an organizer opens the routine and sees which former member is on it, and as what: its requester, its executor, or a place in its rotation.
3. They name a current member as the executor, or take the former member out of the rotation.
4. They make the routine active again. It makes its next occurrence on the first date its schedule gives from that day.
5. The occurrences the routine already made are resolved as tasks, not as routines. See [[tasks/use-cases/08-resolve-a-former-members-tasks]].

## Alternative flows

### The household does not want the routine any more

1. They end it. It is kept, with the record of every turn the former member did. See [[08-end-a-routine]].

### The routine is left paused

1. Nothing happens to it. It makes no occurrence and waits.
2. Nobody is given work they did not agree to, which is the point.

### The former member was only the requester

1. The routine still pauses. The requester is the member who asked for the standing work, and a paused routine asks nobody.
2. The owner or an organizer takes the routine on as its requester, or ends it.

### The rotation still holds enough members

1. The routine still pauses. The household decides whether the turns stay as they were.
2. Taking the former member out of the rotation and making the routine active again carries the turn on from where it was. See [[03-set-a-rotation-on-a-routine]].

## Exception flows

### The routine is made active again with the former member still on it

1. The system refuses and says everybody on a routine must be a member of the household.
2. Nothing changes.

### A member tries to resolve the routine

1. The system refuses and says only the owner and an organizer resolve a routine of a former member.
2. Nothing changes. This is the same authority [[decisions/0005-an-active-task-of-a-former-member-waits]] puts on an unresolved task.

### An organizer resolves a routine whose executor was the owner

1. There is no such routine. An owner who leaves the household hands ownership to another member first, so the owner is never a former member with a routine behind them. See [[household/use-cases/07-transfer-ownership]].

### The former member comes back to the household

1. They are a new member, and the routine does not come back with them. It is resolved or it stays paused.
2. The occurrences they did still name them, as they always did.

## Post-conditions

- The routine is `Active` and names only current members, or `Paused`, or `Ended`
- No member became the executor of the routine without a member with organizer authority deciding it
- The former member is still named on every occurrence they did, and on every comment they wrote
- The occurrences the routine already made are resolved by [[tasks/use-cases/08-resolve-a-former-members-tasks]], not here

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every paused routine in the household, and which former member is on it | Name a new executor, fix the rotation, resume, or end any of them |
| Organizer | Every paused routine in the household, and which former member is on it | Name a new executor, fix the rotation, resume, or end any of them |
| Member | The routines that concern them, and that one they are in is paused | Nothing. A member cannot resolve a routine, not even one they are in the rotation of |
| Minor member | The routines that concern them, and that one they are in is paused | Nothing. A member cannot resolve a routine, not even one they are in the rotation of |

## Applied business rules

- [[rules#a-routine-with-a-former-member-on-it-pauses]] — the routine pauses and waits for organizer authority
- [[rules#pausing-keeps-a-routine-ending-stops-it-for-good]] — a paused routine keeps its turn and its record
- [[rules#an-organizer-cannot-act-on-the-owners-routines]] — why an organizer never meets this case for the owner
- [[tasks/rules#an-unresolved-task-is-a-task-with-a-former-member-on-it]] — the occurrences already made are resolved as tasks
- [[household/rules#a-former-member-stays-on-what-they-left-behind]] — the record is not rewritten
