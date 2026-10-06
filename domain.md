# Domain

Core concepts and vocabulary shared across the product. Terms listed here have a specific meaning in Homehood that may differ from common usage.

Use these words. Do not introduce a synonym for a term that already exists here.

## Household

The group of people who share a home and coordinate their routine together. The household is the boundary of everything in Homehood: a task, an invitation and a member all belong to exactly one household.

"Household" covers a family, a flat share, or any other group under one roof. We do not say "family" for this concept, even though families are the main audience — see [[decisions/0001-household-and-two-member-roles]].

## Member

A person who belongs to a household. A member joins by accepting an invitation.

## Organizer

A member who administers the household. An organizer invites people, removes them, and assigns work to other members. A household has at least one organizer.

Organizer is a permission level, not an age. In a family the parents are usually the organizers. In a flat share it may be one person, or everyone.

## Minor

A member who is under the care of an organizer — in a family, a child. Minor is a property of a member, not a separate permission level, so a household with no minors (a flat share) needs no extra concepts.

Where behavior differs for a minor, the use case says so explicitly in its **By role** section.

## Invitation

An offer from an organizer to a person to become a member of a household. A person is not a member until the invitation is accepted.

## Task

One piece of the household's work, with one owner and one state. A task is the unit everything else attaches to: a comment belongs to a task, and responsibility is expressed by owning a task.

The everyday word for a household task is "chore". In the spec we always say **task**.

## Task state

A task is in exactly one state at a time:

| State | Meaning |
| --- | --- |
| Open | Created, not being worked on |
| Started | Someone is working on it now |
| Closed | The work is finished |
| Archived | Kept for the record, out of the active lists |

Deleting a task removes it. Deleting is not a state.

The rules that govern which transitions are allowed, and who may make them, belong in the module that owns tasks — not here.

## Routine

The recurring part of a household's work: the tasks that come back every day or every week, rather than once.

How recurrence is expressed is not specified yet. The term is listed here because the product is a *routine* manager and the word must mean one thing when we start writing that module.
