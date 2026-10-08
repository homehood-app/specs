# Tasks

The household's work: asking for a task, saying who will do it, and moving it through its states until it is finished — or until it is no longer needed.

This is the module the product exists for. A household with no tasks answers no question.

## Actors

- [[users#owner]] — sees every task in the household, and can act on any of them
- [[users#organizer]] — sees every task in the household, and can act on the work of any member who is not the owner
- [[users#member]] — asks for tasks, does tasks, and sees only the tasks that concern them
- [[users#minor]] — a child who is a member of the household. A member here in every way: this module makes no distinction for a minor

[[users#guardian]] is not an actor in this module. Guardianship is authority over an account, and it reaches no task — see [[accounts/rules#a-guardian-decides-the-account-not-the-household]].

## Responsibilities

- Creating a task, and who its requester and its executor are
- Editing a task
- Starting, commenting on and closing a task
- Archiving a task that was started and is no longer needed
- Deleting a task
- Resolving the active tasks of a member who has left the household
- Who can see which tasks

## Out of scope

- Who belongs to the household. See [[household/overview]].
- Recurrence. [[domain]] names *routine* as the recurring part of the household's work, but how a task repeats is not specified yet.

## Related modules

- [[household/overview]] — a task exists inside one household, and its requester and executor are members of it

## Use cases

[[use-cases/index]]

## Business rules

[[rules]]
