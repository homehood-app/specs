---
decision: 0007
date: 2026-10-08
status: accepted
supersedes:
superseded-by:
---

# 0007 — No age in the product, and one way to a full account

## Question

A household's children are not one kind of person, and they do not stay children. A six-year-old and a sixteen-year-old are both minors, and the sixteen-year-old becomes an adult. Two questions follow, and they have been open since the review of the first pull request: does what a minor can do change with age, and what happens when a child grows up?

## Options

### A — Age bands

Two or more bands, split at an age, each with its own rules.

- **Good:** The product fits the child instead of the category. A teenager stops being treated like an infant without anybody having to act.
- **Cost:** It needs an age, so every minor account needs a date of birth — data the product does not hold, cannot verify, and would have to store for a child. A band also doubles the minor case everywhere: every **By role** table grows a row, and every rule about a minor has to say which band. And the split age is a guess we would defend forever, because no age is right for every household.

### B — No age, and no way to a full account

The product holds no age. A minor account stays a minor account. A child who is ready signs up for their own full account, is invited to the household as a member, and the minor account is removed.

- **Good:** Nothing new to build and nothing to verify. Every piece already exists: sign-up, [[modules/household/use-cases/03-invite-a-person]] and [[modules/household/use-cases/08-remove-a-member]]. The judgement stays with a person instead of with a birthday.
- **Cost:** The person's history does not follow them. Each household ends with a former member — the minor account — and a current member who are the same human, and nothing in the product says so. Two rows for one child, in every home they live in. For a child in two households it is two of each.

### C — No age, and one upgrade the guardian decides

The product holds no age. When the guardian judges the child ready, the minor account **becomes** a full account: the same account, with an email address and a password of its own. Every membership, task and comment stays on it. One way only, and no household is asked.

- **Good:** One identity for one human. The child keeps what they did, in every household at once, and no home has to re-invite anybody. It is also the only answer that does not get worse as the child's life gets more complicated — a child in two homes upgrades once, not twice, and neither household has a say in something that is not theirs to grant.
- **Cost:** It is a feature, where option B was an absence of one. It also sits above a question we have not answered: how a child reaches a minor account at all. And it needs care — the account must not change hands without the child, or a guardian could walk away with somebody's identity.

## Decision

Option C.

- The product holds **no age** for anybody, and no rule anywhere depends on one. There are no age bands
- A minor account **becomes a full account**, once, in one direction. A full account never becomes a minor account
- **The guardian decides it.** No household is asked and no household can refuse — not the owner of the home the child lives in, and not any of the homes if there are several
- **It is the same account.** Every membership, every role, every task where the person is requester or executor, and every comment they wrote is untouched
- **It does not happen without the child.** The guardian asks for it; it finishes only when the account has an email address and a password of its own
- Afterwards the account has no guardian, and cannot be given one
- Becoming a full account is not a promotion. The person is still a plain member of each household, and an owner promotes them afterwards or does not — see [[modules/household/use-cases/06-change-a-members-role]]
- What the child supplies, and how, is part of how a child reaches a minor account, and is not specified yet

## Reason

A band has to be grounded in an age, and an age is the one thing we would have to take on trust. We would collect a date of birth for a child in order to decide which rules apply to them, and we would not be able to check a single one. The cost of the data is larger than the behavior it buys. Holding no age at all is also what lets the guardian be the test: a person who knows the child decides the child is ready, which is both more accurate than a birthday and cheaper than storing one.

An earlier version of this record chose option B, and rejected the upgrade "on order, not on merit" — the argument was that we should not specify the end of a mechanism before its start, because how a minor account is created is still open. That argument was half right and we are not keeping it. *What the child supplies* to finish the upgrade genuinely depends on how a child signs in, and that part stays open and is marked open. But *who decides* and *what survives* do not depend on it at all, and those are the whole decision. Deferring the decision bought nothing and cost the history.

What finally settled it is that option B gets worse with the family, not better. One household, one child: option B costs one awkward pair of rows. A child in two homes, under [[0006-a-minor-is-an-account-kind-not-a-household-role]], costs two — and worse, it asks which of the two homes gets to re-invite the teenager first, which is a question no household should be answering. The upgrade belongs on the account because the account is the only thing in the product that is about the person rather than about a home.

The risk we took care over is the account changing hands. A guardian who could flip a minor account to a full one and keep the credentials would own a second identity. That is why the upgrade finishes with the child supplying the email address and the password, not the guardian: the guardian can start it and cannot complete it. A guardian who wants the child gone has a different act available, and it is honest about what it does — see [[modules/accounts/use-cases/03-delete-a-minor-account]].

We rejected making the upgrade reversible. There is no case for turning a person's own account back into somebody else's, and a reversible one would mean a guardian could take an account back off an adult.

## Affects

- [[domain]] — **Account** changes kind once, in one direction
- [[users]] — the minor persona does not decide this; the guardian persona does
- [[modules/accounts/rules#a-minor-account-becomes-a-full-account-once]] — the rule that carries this decision
- [[modules/accounts/use-cases/02-make-a-minor-account-a-full-account]] — the flow, including the part the child must do
- [[modules/household/rules#a-minor-is-a-member-and-stays-a-member]] — the role does not change here; the kind of account does
- [[modules/household/use-cases/06-change-a-members-role]] — the household's path for "give the child more" is to wait for the guardian, then promote
- [[modules/household/use-cases/07-transfer-ownership]] — a minor cannot receive the household until the account is a full one
- [[templates/module/use-cases/use-case]] — the **By role** table never splits a row by age

## When to revisit

**When somebody has to upgrade an account whose guardian has gone quiet.** Today the guardian is the only route, and a child whose guardian stops answering is stuck. The fix is probably in [[0006-a-minor-is-an-account-kind-not-a-household-role]] — several guardians — rather than here.

**When how a child signs in is specified.** The one open part of this record closes then: what the child supplies to finish the upgrade. The decision itself does not change.

Revisit for age bands only if the product ends up holding a verified date of birth for another reason. The objection here is the cost of the data, and it weakens once the data already exists.
