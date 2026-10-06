---
decision: 0004
date: 2026-10-06
status: accepted
supersedes: 0001-household-and-two-member-roles
superseded-by:
---

# 0004 — Four roles: owner, organizer, member, minor

## Question

[[0001-household-and-two-member-roles]] gave the household two roles — organizer and member — with minor as a property. In review it turned out that one tier of authority is not enough. Who holds the household itself, as opposed to who runs it day to day?

## Options

### A — Keep two roles: organizer and member

- **Good:** The smallest vocabulary. Nothing to learn.
- **Cost:** Every organizer can act on every other organizer, so any organizer can remove the person who created the household. There is nobody who can transfer or delete the household, because no organizer outranks another. The household has no holder.

### B — Three roles: owner, organizer, member

- **Good:** Separates holding the household from running it. Exactly one person can change the household itself, hand it on or end it. Organizers get real authority over people and work without being able to turn on each other or on the owner.
- **Cost:** One more word, and one more rule to remember — an organizer cannot remove a peer.

## Decision

Option B, with minor kept as a property of a member rather than a fourth role.

- **Owner** — one per household. Changes the household's data, hands ownership to another member, deletes the household. Does everything an organizer does. No one can act on them.
- **Organizer** — any number. Invites, removes members, manages the work of other members. Cannot act on the owner, and cannot remove another organizer.
- **Member** — manages themselves and their own work.
- **Minor** — a property of a member. Same authority as their role, reduced view.

## Reason

Two roles left the household without a holder. If every organizer can remove every other organizer, the first organizer can be removed by the person they invited, and nothing in the model says who gets to end the household or hand it on. Those are real acts and they need an owner.

Organizers keep everything that makes the role useful — bringing people in, taking people out, and directing the work — and lose only the ability to turn on a peer or on the owner. That is the narrow restriction that makes the tier safe to hand out.

Minor stays a property rather than a fourth role because it is not a level of authority. A minor holds whatever their role holds and sees less of it. Treating it as a role would have forced a choice between "minor" and "organizer" for a teenager who does both.

## Affects

- [[domain]] — owner, organizer, member and minor
- [[users]] — one persona per role, plus minor
- [[modules/household/rules]] — who can act on whom
- [[templates/module/use-cases/use-case]] — the **By role** table has four rows

## When to revisit

If a household needs more than one owner — two parents who both want to hold it — this record should be superseded by one that allows several owners.
