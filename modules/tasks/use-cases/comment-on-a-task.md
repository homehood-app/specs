---
status: draft
updated: 2026-10-06
superseded-by:
---

# Comment on a task

As a member who can see a task, I want to write on it so that the conversation stays with the work.

**Actors:** [[users#member]], [[users#organizer]], [[users#minor-member]]

## Pre-conditions

- The task exists
- The actor can see it: they own it, they created it, or they are an organizer

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
| Organizer | Every task in the household and every comment on it | Comment on any task in the household |
| Member | The tasks they own and the tasks they created, with their comments | Comment on those tasks |
| Minor member | The tasks they own and the tasks they created, with their comments | Comment on those tasks |

## Applied business rules

- [[rules#a-task-is-visible-to-its-owner-its-creator-and-every-organizer]] — a comment is as visible as its task, and no more
