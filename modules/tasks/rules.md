# Tasks — Business Rules

## Every task has a requester and an executor

They are two roles on the task, not two people. One member asking for their own work is both.

- The requester is the member who asked for the task
- The executor is the member who will do it
- A task has exactly one of each
- Both were members of the household when they were put on the task
- Neither is ever emptied. A member who leaves stays on their tasks

## Any member can request work from any member

Asking is not an act of authority. See [[decisions/0002-any-member-can-give-work-to-another]].

- Any member can create a task with themselves as the executor
- Any member can create a task with any other member as the executor
- A minor member can do both

## The executor works the task

Moving a task through `Started` and `Closed` is the executor's act. Nobody does another member's work for them.

- Only the executor starts their task
- Only the executor closes their task

## A task moves in one direction

| From | To | By |
| --- | --- | --- |
| `Open` | `Started` | the executor begins the work |
| `Started` | `Closed` | the executor finishes the work |
| `Started` | `Archived` | the task is no longer needed |

- An `Open` task cannot be closed. Work is begun before it is finished
- An `Open` task that is no longer needed is deleted, not archived
- `Closed` and `Archived` are final. Neither reopens

## An unresolved task is a task with a former member on it

A task whose requester or executor has left the household keeps them. See [[household/rules#a-former-member-stays-on-what-they-left-behind]].

- A `Closed` or `Archived` task with a former member on it is finished. There is nothing to resolve
- An `Open` or `Started` task with a former member on it is **unresolved**, and waits
- Only a member with organizer authority resolves it: reassign it, archive it, or delete it
- Resolving all of them at once archives every `Started` task and deletes every `Open` one
- A minor is not told that a task of theirs is unresolved. The task stays in their list, unchanged, until somebody with organizer authority resolves it. Waiting on an adult decision is the household's business, not the child's

## A task is visible to its requester, its executor, the owner and every organizer

- The executor sees it
- The requester sees it, even when somebody else is the executor
- The owner and every organizer see every task in the household
- No other member sees it

## A minor sees their own work in full

The minor role takes nothing away from the work. What it reduces is the household — see [[decisions/0006-a-minor-is-reduced-on-the-household-not-on-the-work]].

- A minor sees the same tasks as a plain member: the ones where they are the requester or the executor
- A minor sees who requested the task, who will do it, which state it is in, and every comment on it
- A minor creates, edits, starts, closes, comments on, archives and deletes exactly as a plain member does
- A minor asks any member for work, including an adult. **Any member can request work from any member** holds with no exception for a minor
- A minor sees their closed and archived tasks, which are the record of what they have done
- The one thing a minor does not see is that a task of theirs is **unresolved**

Where a minor names another member — choosing an executor, for example — they are shown names and not roles. See [[household/rules#a-minor-does-not-see-who-runs-the-household]].

## Archiving ends a task that was started

`Archived` is where a task goes when it was begun and then stopped — cancelled, overtaken, or no longer needed. It is kept rather than deleted because by then it carries history.

- Only a task in `Started` can be archived
- A task that was never started is deleted, not archived
- A task that is `Closed` stays closed. Finished is not the same as cancelled

## Who can end a task

- The requester can delete a task that has not been started
- The owner and any organizer can delete any task in the household
- The executor, the requester, the owner and any organizer can archive a started task
- Deleting removes the task and everything attached to it

## An organizer cannot act on the owner's work

Mirrors [[household/rules#authority-over-members-runs-owner-organizer-member-minor]]. Authority over a member's work stops at the owner.

- An organizer can edit, archive or delete the task of any member who is not the owner
- A task whose executor is the owner can be acted on by the owner alone
