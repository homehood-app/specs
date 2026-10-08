---
status: draft
updated: 2026-10-06
superseded-by:
---

# Comment on a task

As a member who can see a task, I want to write on it so that the conversation stays with the work.

**Actors:** [[users#member]], [[users#organizer]], [[users#owner]], [[users#minor]]

## Pre-conditions

- The task exists and is not `Archived`
- The actor can see it

## Main flow

1. The member writes a comment on the task.
2. The system saves it, with who wrote it and when.
3. Everybody who can see the task can see the comment.

## Alternative flows

None.

## Exception flows

### The comment is empty

1. The system refuses and asks for text.
2. No comment is saved.

### The task is archived

1. The system refuses and says an archived task takes no new comments.
2. No comment is saved.

## Post-conditions

- The comment is attached to the task, with its author and its time
- Nobody who cannot see the task can see the comment

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every task in the household and every comment on it | Comment on any task |
| Organizer | Every task in the household and every comment on it | Comment on any task |
| Member | The tasks where they are the requester or the executor, with their comments | Comment on those tasks |
| Minor | The tasks where they are the requester or the executor, with their comments | Comment on those tasks |

## Applied business rules

- [[rules#a-task-is-visible-to-its-requester-its-executor-the-owner-and-every-organizer]] — a comment is as visible as its task, and no more
