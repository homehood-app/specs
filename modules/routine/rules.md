# Routine — Business Rules

## A routine makes tasks and is never one

A routine describes work. An occurrence is the work. See [[decisions/0008-a-routine-is-a-template-that-makes-tasks]].

- A routine holds what the work is, its schedule, and who does it
- A routine has a routine state — `Active`, `Paused` or `Ended` — and never a task state
- A routine is never started and never closed
- Every occurrence is an ordinary task. [[tasks/rules]] governs it from the moment it exists, with no exception
- Closing an occurrence does nothing to the routine. The routine carries on

## An occurrence appears on its due date

The calendar decides, not the occurrence before it. See [[decisions/0009-an-occurrence-appears-on-the-calendar]].

- An `Active` routine makes one occurrence for every date its schedule gives
- The first occurrence is on the routine's start date
- An occurrence appears on its due date whatever happened to the one before it
- A `Paused` or `Ended` routine makes none
- A monthly routine set to a date the month does not have makes its occurrence on the last day of that month
- The occurrence is created in `Open`, with the routine's requester as its requester and the member whose turn it is as its executor

## A routine never has two occurrences waiting

One open occurrence at a time, so that what a member sees today is what they can do today. See [[decisions/0010-one-occurrence-waits-at-a-time]].

- When a routine makes an occurrence, an earlier occurrence of the same routine still in `Open` is deleted, and the routine records a **miss**
- An earlier occurrence in `Started` is left exactly as it is. The routine records no miss, because the work was begun. It stays an ordinary task, and its executor closes it or it is archived
- An earlier occurrence that is `Closed` or `Archived` is finished. There is nothing to record
- A miss belongs to the routine, not to a task. It cannot be done, closed or undone
- Nothing that somebody started is ever deleted, and nothing that nobody started is ever kept. This is [[tasks/rules#archiving-ends-a-task-that-was-started]] read from the routine's side

## The executor of an occurrence is whoever's turn it is

See [[decisions/0011-a-routine-names-one-executor-or-a-rotation]].

- A routine names exactly one executor, or holds a rotation of two or more members. Never both, and never none
- With one executor, every occurrence goes to them
- With a rotation, each occurrence goes to the next member down the list, and the list starts again at the top
- The turn moves when the occurrence is made, not when it is closed. A missed occurrence does not give a member a second turn
- Every member in a rotation is a member of the household, and was when they were put in it
- A member who leaves a rotation does not shift the turns already taken. The record of who did which occurrence stands

## A member sets a routine for themselves; naming another member needs authority

A single task can be asked of anybody. A routine binds somebody's future with no end, and that is not the same act. See [[decisions/0012-a-routine-for-another-member-needs-organizer-authority]].

- Any member can create a routine with themselves as its only executor. A minor can too
- Only the owner and an organizer can create a routine that names another member as its executor
- Only the owner and an organizer can create or change a rotation, because a rotation names other members
- A member can change, pause, end or delete a routine they created for themselves
- The owner and any organizer can change, pause, end or delete any routine in the household
- A member who is the executor of a routine somebody else created cannot change it, pause it or end it. They do each occurrence, and that is the whole of their part
- This narrows nothing in [[tasks/rules#any-member-can-request-work-from-any-member]]. Asking for one task stays open to everybody

## An organizer cannot act on the owner's routines

Mirrors [[household/rules#authority-over-members-runs-owner-organizer-member-minor]] and [[tasks/rules#an-organizer-cannot-act-on-the-owners-work]].

- An organizer can create and change a routine for any member who is not the owner
- A routine whose executor is the owner can be acted on by the owner alone
- An organizer cannot put the owner into a rotation, and cannot remove the owner from one. The owner does that

## A routine with a former member on it pauses

Mirrors [[decisions/0005-an-active-task-of-a-former-member-waits]], applied to a thing that points forwards. See [[decisions/0013-a-routine-with-a-former-member-on-it-pauses]].

- A member is **on** a routine when they are its requester, its executor, or in its rotation
- When a member on a routine stops being a member, the routine pauses at once and makes no further occurrence
- It pauses even when the rotation still holds enough members to carry on. The household decides whether the turns stay as they were
- Occurrences the routine already made keep the former member and follow [[tasks/rules#an-unresolved-task-is-a-task-with-a-former-member-on-it]]
- A member with organizer authority resolves the routine: give it a new executor or fix its rotation and make it active again, or end it
- The routine keeps the former member on the occurrences they did. A record of what happened is not rewritten — see [[household/rules#a-former-member-stays-on-what-they-left-behind]]

## Pausing keeps a routine; ending stops it for good

- A `Paused` routine keeps its schedule, its executor or rotation, its turn and its record. Making it active again resumes the schedule from that day. It does not make the occurrences the pause skipped, and it records no miss for them
- `Ended` is final. An ended routine never becomes active again. The household writes a new routine instead
- Ending a routine deletes its waiting occurrence, if it has one, and leaves every other occurrence exactly as it is
- A routine that made at least one occurrence is ended, not deleted
- A routine that never made an occurrence is deleted. Deleting removes the routine and its record of misses

## A routine is visible to the people its occurrences are visible to

[[decisions/0003-a-member-sees-only-their-own-tasks]], applied to the routine itself.

- Its executor sees it. Every member in its rotation sees it
- Its requester sees it, even when somebody else does the work
- The owner and every organizer see every routine in the household
- No other member sees it
- Who sees an occurrence is decided by [[tasks/rules#a-task-is-visible-to-its-requester-its-executor-the-owner-and-every-organizer]] and nothing here. A member in a rotation sees the routine, and sees only the occurrences that fell to them
