---
decision: 0007
date: 2026-10-07
status: accepted
supersedes:
superseded-by:
---

# 0007 — No age in the product, and no conversion of a minor account

## Question

A household's children are not one kind of person, and they do not stay children. A six-year-old and a sixteen-year-old are both minors, and the sixteen-year-old becomes an adult. Two questions follow, and they have been open since the review of the first pull request: does what a minor can do change with age, and what happens when a child grows up?

## Options

### A — Age bands

Two or more bands, split at an age, each with its own rules.

- **Good:** The product fits the child instead of the category. A teenager stops being treated like an infant without anybody having to act.
- **Cost:** It needs an age, so every minor account needs a date of birth — data the product does not hold, cannot verify, and would have to store for a child. A band also doubles the minor case everywhere: every **By role** table grows a row, and every rule about a minor has to say which band. And the split age is a guess we would defend forever, because no age is right for every household.

### B — Conversion: a minor account becomes a full account

When the child is ready, the household or the child turns the minor account into a full account. The history comes with it.

- **Good:** The person keeps everything — their tasks, their comments, the record of what they did. One identity for one human.
- **Cost:** It is a whole feature, and it sits on top of a question we have not answered. A minor account needs no email address and signs in some way we have not specified yet — see [[0006-a-minor-is-an-account-kind-not-a-household-role]]. Converting an account whose creation is undefined means specifying both at once. It also needs care we have not designed: who may start it, whether the child consents, and what stops a parent from taking an adult's account over by the same route.

### C — No age and no conversion

The product holds no age. A minor account stays a minor account. A child who is ready signs up for their own full account, is invited to the household as a member, and the minor account is removed.

- **Good:** Nothing new to build and nothing to verify. Every piece already exists: sign-up, [[modules/household/use-cases/03-invite-a-person]], and [[modules/household/use-cases/08-remove-a-member]]. The judgement stays with the parent, where it belongs, instead of with a birthday.
- **Cost:** The person's history does not follow them. The household keeps a former member — the minor account — that is the same human as the new member, and nothing in the product says so. Two rows for one child.

## Decision

Option C.

- The product holds no age for a minor, and no rule anywhere depends on one. There are no age bands
- A minor account is never converted. There is no path from a minor account to a full account
- A child who is ready for their own account gets one the ordinary way: they sign up, a member with organizer authority invites them, they accept as a member, and the household removes the minor account
- The work the minor account did stays on the minor account, which becomes a former member — see [[modules/household/rules#a-former-member-stays-on-what-they-left-behind]]

## Reason

A band has to be grounded in an age, and an age is the one thing we would have to take on trust. We would collect a date of birth for a child in order to decide which rules apply to them, and we would not be able to check a single one. The cost of the data is larger than the behavior it buys.

Conversion was rejected on order, not on merit. It is the right answer eventually and it is the wrong thing to specify now, because the account it converts does not have a specified beginning yet. First we decide how a minor account is made and how a child signs in; then conversion is a small step from there. Doing it the other way round means designing the end of a mechanism before its start.

What makes option C acceptable is that the path exists today and costs the household one act. A teenager signing up with their own email address is not a workaround — it is the honest moment a person stops being somebody else's account and starts being their own. The product does not have to invent anything to let that happen.

The cost is the history, and it is real: the household ends with a former member and a current member who are the same child, and nothing links them. We take it because the alternative is a feature built on an undefined foundation, and because the record of what somebody did as a child is not what a sixteen-year-old is asking for when they ask for their own account.

## Affects

- [[users]] — the minor persona says the role does not change with age, and there is no conversion
- [[domain]] — **Account** holds no age, and the two kinds do not change into one another
- [[modules/household/rules#a-minor-is-a-member-and-stays-a-member]] — the role never changes
- [[modules/household/use-cases/06-change-a-members-role]] — a minor's role cannot be changed, and the use case refuses it
- [[templates/module/use-cases/use-case]] — the **By role** table never splits a row by age

## When to revisit

**When how a minor signs in is specified.** Conversion becomes a small, honest feature at that point, and this record should be superseded by one that adds it. That is the expected end of this decision, not a remote possibility.

**When a household loses a child's history this way and tells us it hurts.** One household doing it is a conversation. Several mean the cost we accepted is bigger than we judged.

Revisit for age bands only if the product ends up holding a verified date of birth for another reason. The objection here is the cost of the data, and it weakens once the data already exists.
