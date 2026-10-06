# Tasks — Business Rules

## Every task has a requester and an executor

They are two roles on the task, not two people. One member asking for their own work is both.

- The requester is the member who asked for the task
- The executor is the member who will do it
- A task has exactly one of each
- Both are members of the same household as the task

## Any member can request work from any member

Asking is not an act of authority. See [[decisions/0002-any-member-can-give-work-to-another]].

- Any member can create a task with themselves as the executor
- Any member can create a task with any other member as the executor
- A minor member can do both

## The executor works the task

Moving a task through `Started` and `Closed` is the executor's act. Nobody does another member's work for them.

- Only the executor starts their task
- Only the executor closes their task

## A task is visible to its requester, its executor, the owner and every organizer

- The executor sees it
- The requester sees it, even when somebody else is the executor
- The owner and every organizer see every task in the household
- No other member sees it

## Archiving ends a task that was started

`Archived` is where a task goes when it was begun and will not be finished — cancelled, overtaken, no longer wanted. It is kept rather than deleted because by then it carries history.

- Only a task in `Started` can be archived
- A task that was never started is deleted, not archived
- A task that is `Closed` stays closed. Finished is not the same as abandoned

## Who can end a task

- The requester can delete a task that has not been started
- The owner and any organizer can delete any task in the household
- The executor, the requester, the owner and any organizer can archive a started task
- Deleting removes the task and everything attached to it

## An organizer cannot act on the owner's work

Mirrors [[household/rules#authority-over-members-runs-owner-organizer-member]]. Authority over a member's work stops at the owner.

- An organizer can edit, archive or delete the task of any member who is not the owner
- A task whose executor is the owner can be acted on by the owner alone
