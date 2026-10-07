# Domain

Core concepts and vocabulary shared across the product. Terms listed here have a specific meaning in Homehood that may differ from common usage.

Use these words. Do not introduce a synonym for a term that already exists here.

## Household

The group of people who share a home and coordinate their routine together. The household is the boundary of everything in Homehood: a task, an invitation and a member all belong to exactly one household.

"Household" covers a family, a flat share, or any other group under one roof. We do not say "family" for this concept, even though families are the main audience — see [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].

A person can belong to several households at the same time. Nothing stops it, unless they hold a minor account.

## Account

What a person signs in with. A full account exists outside any household: it is made before joining one and it survives leaving one. A minor account is the exception on both counts — the household makes it, and it ends with the membership.

There are two kinds, and an account never changes kind — see [[decisions/0007-no-age-and-no-conversion-of-a-minor-account]].

| Kind | Who holds it | How it begins |
| --- | --- | --- |
| Full account | Anybody who signs themselves up | The person creates it themselves |
| Minor account | A child of one household | The household creates it for them |

A full account is the ordinary one. It belongs to the person who made it, it can be a member of any number of households, and it can hold any role.

A minor account is made for a child by the household they live in. It needs no email address of its own. It belongs to exactly one household, always holds the member role, and cannot be made a full account. How it is created, and how a child signs in to it, is not specified yet.

We do not say "user" for this. The person is a **member** of a household; the thing they sign in with is an **account**.

## Member

A person who belongs to a household. A member joins by accepting an invitation, or is a minor the household created inside it.

Every member holds exactly one role: owner, organizer or member. A minor always holds the member role.

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

A member who holds a minor account — in a family, a child. Minor is not a role: it is what the account is. See [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].

A minor is a member and does everything a member does, with nothing taken away. Five things are true of a minor and of nobody else:

- They belong to exactly one household
- They cannot leave it. Only a member with organizer authority takes them out
- They cannot hold the owner role
- They cannot hold the organizer role
- They cannot become a full account, at any age — see [[decisions/0007-no-age-and-no-conversion-of-a-minor-account]]

A flat share has no minors. A household with no children has none either.

## Invitation

An offer from an owner or an organizer to a person, to become a member of a household. A person is not a member until the invitation is accepted.

An invitation reaches a person through an account of their own, so a minor is never invited. A minor is created inside the household they belong to, and is a member from that moment.

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
