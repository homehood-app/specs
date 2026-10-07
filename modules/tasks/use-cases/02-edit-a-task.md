---
status: draft
updated: 2026-10-06
superseded-by:
---

# Edit a task

As a member who can see a task, I want to change what it says so that it describes the real work.

**Actors:** [[users#member]], [[users#organizer]], [[users#owner]], [[users#minor-member]]

## Pre-conditions

- The task exists and is not `Archived`
- The actor can see it

## Main flow

1. The member changes the description of the task.
2. The system saves the change.

## Alternative flows

### The executor is changed

1. The member chooses a different member of the household as the executor.
2. The system changes the executor.
3. The previous executor stops seeing the task, unless they are the requester, the owner or an organizer.
4. If the task was `Started`, the system returns it to `Open`. Nobody inherits work already begun by somebody else.

### An organizer edits another member's task

1. They can, on any task in the household except one where the owner is the executor.

## Exception flows

### The task is archived

1. The system refuses and says an archived task cannot be edited.
2. Nothing changes.

### The new executor is not a member of the household

1. The system refuses and says the person is not in this household.
2. Nothing changes.

## Post-conditions

- The task says what the editor wrote
- The task still has exactly one requester and one executor, both members of the household
- A task whose executor changed is not `Started`

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every task in the household | Edit any task, including its executor |
| Organizer | Every task in the household | Edit any task except one where the owner is the executor |
| Member | The tasks where they are the requester or the executor | Edit those tasks, including the executor |
| Minor member | The tasks where they are the requester or the executor | Edit those tasks, including the executor |

## Applied business rules

- [[rules#a-task-is-visible-to-its-requester-its-executor-the-owner-and-every-organizer]] — you can only edit what you can see
- [[rules#every-task-has-a-requester-and-an-executor]] — changing the executor replaces them, it does not add one
- [[rules#an-organizer-cannot-act-on-the-owners-work]] — an organizer stops at the owner
