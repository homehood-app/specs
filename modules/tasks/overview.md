# Tasks

The household's work: creating a task, saying whose it is, and moving it through its states until it is finished and put away.

This is the module the product exists for. A household with no tasks answers no question.

## Actors

- [[users#organizer]] — sees every task in the household, and is the only role that can delete one
- [[users#member]] — creates tasks, owns tasks, and works them
- [[users#minor-member]] — a member under the care of an organizer

## Responsibilities

- Creating a task, for yourself or for another member
- Editing a task
- Starting, commenting on and closing a task
- Archiving a task, and deleting a task
- Who can see which tasks

## Out of scope

- Who belongs to the household. See [[household/overview]].
- Recurrence. [[domain]] names *routine* as the recurring part of the household's work, but how a task repeats is not specified yet.

## Related modules

- [[household/overview]] — a task exists inside one household and is owned by one of its members

## Use cases

[[use-cases/index]]

## Business rules

[[rules]]
