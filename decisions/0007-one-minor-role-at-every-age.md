---
decision: 0007
date: 2026-10-07
status: accepted
supersedes:
superseded-by:
---

# 0007 — One minor role at every age

## Question

A household's children are not one kind of person. A six-year-old and a sixteen-year-old are both minors, and the gap between them is wider than the gap between the older one and an adult. Does what a minor sees and can do change with age? This question was raised in the review of the first pull request and stayed open through the second.

## Options

### A — Age bands

Two or more bands, split at an age — a younger child and an older child — each with its own rules.

- **Good:** The product fits the child instead of the category. A teenager stops being treated like an infant without anybody having to act.
- **Cost:** It needs an age, so every minor needs a date of birth: data the product does not hold, cannot verify, and would have to store for a child. A band also doubles the minor case everywhere — every **By role** table grows a row, and every rule that mentions a minor has to say which band. And the split age is a guess we would be defending forever, because no age is the right one for every household.

### B — One minor role at every age

One minor role. The household moves a child who is ready to the plain member role.

- **Good:** No date of birth, nothing to verify, nothing to store. One minor row per **By role** table. The lever is the household's rather than the product's: the owner decides when a child is ready, which is a judgement a parent makes well and a date makes badly. The mechanism already exists — it is [[modules/household/use-cases/06-change-a-members-role]], the same use case that promotes and demotes anybody.
- **Cost:** Nothing happens on its own. A child who grows up stays a minor until somebody notices, and no household is reminded. The step is also all-or-nothing: the owner moves a child to a plain member in full, and cannot grant a part of it.

### C — Per-minor switches

No bands. The owner turns individual permissions on or off for each minor.

- **Good:** The most exact fit. Each household tunes each child as far as it wants.
- **Cost:** It is a permission system, and the product does not have one. Every use case would have to name the switch that governs it, the **By role** table stops being able to answer anything on its own, and the household gets a settings screen to maintain instead of a role to choose. A large amount of machinery for a product whose first rule is that a member sees their own work.

## Decision

Option B. One minor role, at every age. The behavior of a minor never changes by itself.

A child who is ready for more becomes a plain member, by a role change the owner makes. The reverse is the same act.

The product holds no age for a minor, and no rule anywhere depends on one.

## Reason

A band has to be grounded in an age, and an age is the one thing we would have to take on trust. We would be collecting a date of birth for a child in order to decide whether to hide the name of the household's owner from them. The cost of the data is larger than the behavior it buys.

The household already has a better instrument. "Is this child ready to see and run their own part of the home?" is a question a parent answers from what they know, not from arithmetic on a birthday. [[0004-four-roles-owner-organizer-member-minor]] already made growing up a role change, so choosing this option adds no mechanism at all — it only declines to add one.

Per-minor switches were rejected for size, not for value. They are the right shape eventually; they are the wrong thing to build before the product has a single rule that varies by minor. Today there are two.

The real cost is that nothing happens automatically, and it is accepted: a household that forgets to promote a teenager keeps a teenager who sees slightly less. That is a small harm, and it is reversible in one act.

## Affects

- [[users]] — the Minor member persona says the role does not change with age
- [[domain]] — Minor carries the same statement
- [[modules/household/use-cases/06-change-a-members-role]] — the owner moves a child who has grown up to the plain member role
- [[templates/module/use-cases/use-case]] — the **By role** table keeps one minor row, and never splits by age

## When to revisit

When a household asks for a part of the member role for a child, rather than all of it. One such request is a conversation; several mean option C has become worth its size, and this record should be superseded by one that adds per-minor permissions — not by one that adds an age.

If the product ever needs a date of birth for another reason, revisit as well. The objection here is the cost of the data, and that objection weakens once the data already exists.
