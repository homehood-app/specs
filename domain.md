# Domain

Core concepts and vocabulary shared across the product. Terms listed here have a specific meaning in Homehood that may differ from common usage.

Use these words. Do not introduce a synonym for a term that already exists here.

## Household

The group of people who share a home and coordinate their routine together. The household is the boundary of everything in Homehood: a task, an invitation and a membership all belong to exactly one household. A person can hold a membership in several, and each one shows them only its own home.

"Household" covers a family, a flat share, or any other group under one roof. We do not say "family" for this concept, even though families are the main audience — see [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].

A person can belong to several households at the same time. Nothing stops it, and a minor is no exception — a child of separated parents belongs to both homes.

## Account

What a person signs in with. An account exists outside any household: it is there before the first membership and it survives the last one.

There are two kinds. An account changes kind once, in one direction only — see [[decisions/0007-no-age-and-one-way-to-a-full-account]].

| Kind | Who holds it | How it begins | Who is responsible for it |
| --- | --- | --- | --- |
| Full account | Anybody who signs themselves up | The person creates it themselves | Its own holder |
| Minor account | A child | A full account creates it for them | Its guardian |

A full account is the ordinary one. It belongs to the person who made it, it can be a member of any number of households, it can hold any role, and nobody else answers for it.

A minor account is made for a child by a full account, which becomes its **guardian** by that act, and it needs no email address of its own. The child reaches it with a name of its own kind and a short secret, neither of them an email address or a password — see [[modules/accounts/domain]] and [[decisions/0014-a-child-signs-in-with-a-handle-and-a-pin]]. It can be a member of any number of households and always holds the member role in each one. It cannot choose where it belongs and cannot walk away: its guardian does both for it.

We do not say "user" for this. The person is a **member** of a household; the thing they sign in with is an **account**.

## Member

A person who belongs to a household. A member joins by accepting an invitation — for a minor, the guardian accepts it.

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

A person who holds a minor account — in a family, a child. Minor is not a role: it is what the account is. See [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].

In every household they belong to, a minor is a member and does everything a member does, with nothing taken away. Four things are true of a minor and of nobody else:

- They do not decide where they belong. Their guardian accepts an invitation for them
- They cannot leave a household. Organizer authority in that household takes them out, and so can their guardian
- They cannot hold the owner role
- They cannot hold the organizer role

A minor account becomes a full account one day, and its guardian decides when — see [[decisions/0007-no-age-and-one-way-to-a-full-account]]. Nothing about a minor depends on an age, because the product holds none.

A flat share has no minors. A household with no children has none either.

## Guardian

The full account responsible for a minor account. In a family, a parent.

Every minor account has exactly one guardian, and never none. A guardian is the account that made it, until guardianship is handed to another full account. One guardian can hold several minor accounts; a minor account cannot be a guardian.

Guardianship is a relationship between two accounts, outside every household. It is not a role, it gives no authority inside any household, and it lets its holder see nothing that their own membership does not already show them. What a guardian decides is the account: where it belongs, when it leaves, when it becomes a full account, and when it ends. See [[modules/accounts/overview]].

## Invitation

An offer from an owner or an organizer to a person, to become a member of a household. A person is not a member until the invitation is accepted.

An invitation to a full account is answered by its holder. An invitation to a minor account is answered by its guardian, because a child does not choose which homes they live in — and it is addressed to the guardian too, because a minor account holds nothing a household could send to.

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
