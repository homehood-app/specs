# Domain

Core concepts and vocabulary shared across the product. Terms listed here have a specific meaning in Homehood that may differ from common usage.

Use these words. Do not introduce a synonym for a term that already exists here.

## Household

The group of people who share a home and coordinate their routine together. The household is the boundary of everything in Homehood: a task, an invitation and a member all belong to exactly one household.

"Household" covers a family, a flat share, or any other group under one roof. We do not say "family" for this concept, even though families are the main audience — see [[decisions/0004-four-roles-owner-organizer-member-minor]].

A person can belong to several households at the same time. Nothing stops it.

## Member

A person who belongs to a household. A member joins by accepting an invitation.

Every member holds exactly one role: owner, organizer, member or minor.

## Former member

A person who was a member of a household and is not any more. A former member sees nothing of the household.

The household keeps them on what they left behind. A task they requested or executed still names them, and so does every comment they wrote. A record of what happened is not rewritten because somebody left.

## Owner

The member who holds the household. Exactly one per household, and the household cannot exist without one.

The owner is the only member who can change the household itself — its data, its ownership and its existence. The owner can do everything an organizer can do, and the owner is the only member no organizer can act upon.

## Organizer

A member who runs the household's day-to-day on the owner's behalf. A household can have any number of organizers, including none.

An organizer manages members and tasks. An organizer cannot act on the owner, and cannot remove another organizer.

## Minor

The lowest role. A member under the care of the household — in a family, a child.

A minor does what a plain member does over the work, with nothing taken away. What is reduced is the household: a minor does not see who the owner is, does not see which members are organizers, and cannot take themselves out of a household — see [[decisions/0006-a-minor-is-reduced-on-the-household-not-on-the-work]].

The role does not change with age. A child who is ready for more becomes a plain member, by a role change — see [[decisions/0007-one-minor-role-at-every-age]].

There is no minor owner and no minor organizer. A minor who grows into either stops being a minor, by a role change — see [[decisions/0004-four-roles-owner-organizer-member-minor]].

## Invitation

An offer from an owner or an organizer to a person, to become a member of a household. A person is not a member until the invitation is accepted.

## Task

One piece of the household's work. A task is the unit everything else attaches to: a comment belongs to a task, and responsibility is expressed by the two people attached to it.

The everyday word for a household task is "chore". In the spec we always say **task**.

## Requester

The member who asked for the task. The requester wants the work done, and is not necessarily the person who will do it.

## Executor

The member who will do the task. Exactly one per task.

The requester and the executor are often the same person — someone opening a task for themselves is both.

## Task state

A task is in exactly one state at a time:

| State | Meaning |
| --- | --- |
| Open | Asked for, not begun |
| Started | The executor is working on it |
| Closed | The work is finished |
| Archived | It was begun and will not be finished. Kept for what it holds |

`Archived` is not "tidied away". It is the end of a task that was started and then stopped, because it was cancelled or is no longer needed. We keep it instead of deleting it because by then it carries history — comments, who started it, when.

A task that was never started and is no longer needed is deleted, not archived. There is nothing in it worth keeping.

Deleting a task removes it. Deleting is not a state.

The rules that govern which transitions are allowed, and who may make them, belong in the module that owns tasks — not here.

## Routine

The recurring part of a household's work: the tasks that come back every day or every week, rather than once.

How recurrence is expressed is not specified yet. The term is listed here because the product is a *routine* manager and the word must mean one thing when we start writing that module.
