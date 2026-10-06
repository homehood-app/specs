---
status: draft
updated: 2026-10-06
superseded-by:
---

# Edit a task

As a member who can see a task, I want to change what it says so that it describes the real work.

**Actors:** [[users#member]], [[users#organizer]], [[users#minor-member]]

## Pre-conditions

- The task exists
- The actor can see it: they own it, they created it, or they are an organizer

## Main flow

1. The member changes the description of the task.
2. The system saves the change.

## Alternative flows

### The owner is changed

1. The member chooses a different member of the household as the owner.
2. The system changes the owner.
3. The previous owner no longer sees the task, unless they created it or are an organizer.

## Exception flows

### The task is archived

1. The system refuses and says an archived task cannot be edited.
2. Nothing changes.

### The new owner is not a member of the household

1. The system refuses and says the person is not in this household.
2. Nothing changes.

## Post-conditions

- The task says what the editor wrote
- The task still has exactly one owner, who is a member of the household

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Organizer | Every task in the household | Edit any task in the household, including its owner |
| Member | The tasks they own and the tasks they created | Edit those tasks, including the owner |
| Minor member | The tasks they own and the tasks they created | Edit those tasks, including the owner |

## Applied business rules

- [[rules#a-task-is-visible-to-its-owner-its-creator-and-every-organizer]] — you can only edit what you can see
- [[rules#a-task-has-exactly-one-owner]] — changing the owner replaces it, it does not add one
