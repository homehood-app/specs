---
decision: 0006
date: 2026-10-07
status: accepted
supersedes: 0004-four-roles-owner-organizer-member-minor
superseded-by:
---

# 0006 — A minor is an account kind, not a household role

## Question

[[0004-four-roles-owner-organizer-member-minor]] made minor the fourth rung of the household's ladder: owner, organizer, member, minor. Writing down what the fourth rung actually narrows showed that almost nothing about a minor is about the household. What is different about a child is the **account**: a child does not sign up, does not hold an email address, does not shop for households to join, and does not get to walk out of the one they live in. A parent makes the account for them.

So where does minor belong — on the household's ladder, or on the account?

## Options

### A — A fourth household role

Minor is the lowest rung: owner, organizer, member, minor. Every person signs up the same way, and the household decides what a person is once they are inside it.

- **Good:** One ladder, one list, nothing new to name. The **By role** table answers the minor case in every use case, because minor has a row.
- **Cost:** It puts the difference in the wrong place and so cannot express the difference at all. A role says what a person may do *inside a household*. It cannot say "this person needs no email address", "this person signs in another way", or "this person exists in one household and nowhere else" — those are facts about an account, and a role has no way to hold them. Worse, as a role it implies a child signs themselves up like everybody else and is then labelled, which is not how a child gets into a family app.

### B — A kind of account

Three household roles — owner, organizer, member. A minor is a kind of **account**, created by the household for a child, that always holds the member role.

- **Good:** Each fact lands where it belongs. The account carries what is different about a child — no email address, made by a parent, one household, no way out on their own. The role carries what is the same — a minor is a member and does a member's work. The household's ladder goes back to three rungs, each a real tier of authority, with nothing on it that is not about authority.
- **Cost:** Two concepts to hold instead of one, and a reader has to learn that "minor" and "member" are answers to different questions. The **By role** table also needs a minor row that is not a role, or the minor case stops being answered.

### C — Both: a minor account and a minor role

The account kind for the sign-in facts, plus a fourth role for the in-household restrictions.

- **Good:** Nothing is squeezed into the wrong concept.
- **Cost:** Two things to keep in step for one person, and the role would carry a single rule — a minor is a member who cannot be promoted — which the account kind already implies, because an account made for a child is not a household's organizer.

## Decision

Option B.

**The household has three roles:** owner, organizer, member. In that order of authority. Everything [[0004-four-roles-owner-organizer-member-minor]] settled about the owner stands, and so does the neutral vocabulary from [[0001-household-and-two-member-roles]]: we say household, not family.

**A minor is a kind of account**, made by the household for a child who lives in it. A minor always holds the member role, and a minor's authority over the work is a plain member's, in full.

What is true of a minor and of nobody else:

- A minor belongs to exactly one household
- A minor cannot leave a household. Only a member with organizer authority takes them out
- A minor cannot hold the owner role
- A minor cannot hold the organizer role
- A minor cannot become a full account. There is no conversion — see [[0007-no-age-and-no-conversion-of-a-minor-account]]

Everything else about a minor is a plain member's, including what they see. A minor sees who the owner is, sees which members are organizers, and sees their own work exactly as any member does.

Out of scope here, deliberately: how a minor account is created, and how a child signs in to it. A minor account needs no email address and no password of the usual kind, and the mechanism is a separate question.

## Reason

The test that decided it was a single question: can a role say "this person needs no email address"? It cannot. A role is a statement about authority inside one household, and the things that make a child different are statements about the account — who made it, what it needs to exist, how many households it can ever be in, and whether its holder can walk away. Putting them on a role meant they could not be written down at all, which is exactly what happened: the fourth rung sat in the spec for two pull requests with nothing in it.

Moving minor onto the account also fixed the ladder. Owner, organizer and member are three tiers of authority, each one able to do something the next cannot. "Minor" was never that: it was a member with a different front door. A ladder that mixes authority with provenance is a ladder that cannot be reasoned about.

The cost of option B is real and we pay it: a reader has to hold two concepts. It is worth it because the alternative is a spec that silently implies children sign themselves up with an email address, which no family app does.

Option C was rejected for size. The in-household restrictions that would have justified a second concept come to one sentence — a minor is a member and cannot be promoted — and that sentence belongs with the account, which is what makes it true.

The restrictions we considered and left out are as important as the ones we kept. A minor does not see less of the household: not the roles of other members, not who the owner is, not whether a task of theirs is waiting on an adult. Those were in an earlier draft of this record and they are gone, because a restriction is worth writing only when it changes what somebody can do. Hiding a label on a screen does not.

## Affects

- [[domain]] — **Account** is a new concept with two kinds; Minor is an account kind; Member holds one of three roles
- [[users]] — three roles plus the minor persona, which is an account kind and not a rung
- [[modules/household/rules#a-minor-is-a-member-and-stays-a-member]] — no promotion, no ownership
- [[modules/household/rules#a-minor-belongs-to-one-household-and-cannot-leave-it]] — one household, and only removal takes them out
- [[modules/household/rules#membership-starts-with-an-accepted-invitation-or-with-a-minor-the-household-creates]] — the second door into a household
- [[modules/household/use-cases/01-create-a-household]] — a minor cannot start one
- [[modules/household/use-cases/03-invite-a-person]] — a minor is not invited, and cannot be
- [[modules/household/use-cases/05-answer-an-invitation]] — a minor has nothing to answer
- [[modules/household/use-cases/06-change-a-members-role]] — a minor's role cannot change
- [[modules/household/use-cases/07-transfer-ownership]] — a minor cannot receive the household
- [[modules/household/use-cases/08-remove-a-member]] — the only way a minor leaves
- [[modules/household/use-cases/09-leave-a-household]] — a minor is refused
- [[modules/household/use-cases/10-delete-a-household]] — a minor account ends with the household that holds it
- [[modules/tasks/rules#a-minor-works-like-any-other-member]] — nothing in the work is reduced
- [[templates/module/use-cases/use-case]] — the **By role** table keeps four rows: three roles, and a minor row that is not a role

## When to revisit

**When the product holds money.** A household budget is the first thing we expect a minor not to see, and it is the restriction Tiago named. It does not need a new record — it needs a rule in the module that owns money, and a minor row that says `Nothing.`

**When a child lives in two homes.** Shared custody breaks "exactly one household" and nothing else in this record. That is a new record, and it is the most likely reason this one changes.

**When a minor has to grow up with their history.** Today a teenager gets a full account of their own and is invited as a member, and the work the minor account did stays on the minor account — see [[0007-no-age-and-no-conversion-of-a-minor-account]].
