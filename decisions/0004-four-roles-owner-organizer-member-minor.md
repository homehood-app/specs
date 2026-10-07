---
decision: 0004
date: 2026-10-07
status: accepted
supersedes: 0001-household-and-two-member-roles
superseded-by:
---

# 0004 — Four roles: owner, organizer, member, minor

## Question

[[0001-household-and-two-member-roles]] gave the household two roles — organizer and member — with minor as a property of a member. Two things turned out to be wrong with that. One tier of authority leaves nobody holding the household, and treating minor as a property invents combinations the product will never have. How many roles are there, and is minor one of them?

## Options

### A — Two roles, organizer and member, with minor as a property

- **Good:** The smallest vocabulary.
- **Cost:** Every organizer can act on every other organizer, so any organizer can remove the person who created the household. Nobody can transfer or delete the household, because no organizer outranks another. The household has no holder.

### B — Three roles, owner, organizer and member, with minor still a property

- **Good:** Fixes the holder. Exactly one person can change the household itself, hand it on or end it.
- **Cost:** Keeps minor on a second axis, which implies a minor owner and a minor organizer are possible. They are not. It also gives a spec author nothing to fill in: the minor case has to be remembered rather than answered.

### C — Four roles: owner, organizer, member, minor

- **Good:** One ladder, four rungs, no second axis. A minor is a member with less, which is exactly what a minor is. The **By role** table has a row per role, so the minor case is answered in every use case instead of remembered. A child growing up is a role change, which the household already knows how to do.
- **Cost:** If a minor ever needs to run the household — an older teenager as an organizer — the model has to change rather than just the data.

## Decision

Option C. Four roles, in this order of authority:

- **Owner** — one per household. Changes the household's data, hands ownership to another member, deletes the household, sets everybody's role. Does everything an organizer does. No one can act on them.
- **Organizer** — any number. Invites, removes members, manages the work of other members. Cannot act on the owner, and cannot remove another organizer.
- **Member** — manages themselves and their own work.
- **Minor** — does what a member does, and sees less of it.

## Reason

Two roles left the household without a holder. If every organizer can remove every other organizer, the first organizer can be removed by the person they invited, and nothing says who gets to end the household or hand it on. Those are real acts and they need an owner.

Minor became a role rather than a property because the property was describing something that does not exist. A minor owner and a minor organizer do not make sense: a minor is always a member with less. Modelling it as a second axis would have created four combinations where the product only ever has one, and the spec would have had to keep explaining that three of them cannot happen.

As a role it also earns its row in the **By role** table of every use case. That is the difference between a minor's behavior being answered and being forgotten.

A child who grows up changes role, through the same use case that promotes and demotes anybody else.

## Affects

- [[domain]] — owner, organizer, member and minor
- [[users]] — one persona per role
- [[modules/household/rules#authority-over-members-runs-owner-organizer-member-minor]] — who can act on whom
- [[modules/household/use-cases/06-change-a-members-role]] — a minor becomes a member by a role change
- [[templates/module/use-cases/use-case]] — the **By role** table has four rows, one per role

## When to revisit

If a minor needs to run the household — an older teenager as an organizer — this record should be superseded by one that puts care back on its own axis. The same applies if a household needs more than one owner.
