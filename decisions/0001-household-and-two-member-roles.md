---
decision: 0001
date: 2026-10-06
status: superseded
supersedes:
superseded-by: 0004-four-roles-owner-organizer-member-minor
---

# 0001 — Household, not family, and two member roles

## Question

Families are the main audience, but a flat share or any group under one roof has the same problem and would use the product the same way. What do we call the group, and what do we call the people in it?

## Options

### A — Household, with Organizer and Member, and minor as a property of a member

- **Good:** Two role names cover both audiences with no extra concepts. A flat share is a household of members where one or more are organizers, and it never has to think about minors. A family is the same structure with the parents as organizers and the children marked as minors. "Household" is also the plain, standard word for the concept, so nobody has to learn it.
- **Cost:** "Organizer" is a word the team has to adopt; nobody says it at home. A minor being a property rather than a role means a spec author must remember to state the minor's behavior, instead of being handed an empty row to fill.

### B — Household, with three roles: Organizer, Adult, Child

- **Good:** Nothing to remember. The **By role** table has a row per role, so a spec author cannot skip the child case.
- **Cost:** Mixes two different things in one axis — what you are allowed to do, and whether you are under someone's care. A housemate who is not an organizer and a parent who is not an organizer are both just "Adult", which hides a real difference. It also puts "Child" in the vocabulary of a flat share that has none.

### C — Family, with Parent and Child

- **Good:** The warmest and most natural words. It matches the main audience exactly, and needs no abstraction today.
- **Cost:** Wrong for every household that is not a family, which is a use we already expect. Renaming the central domain term later is the most expensive change a spec can take: it touches every file, every rule and every use case.

## Decision

Option A. The group is a **household**. Its people are **members**. A member who administers the household is an **organizer**. Being a **minor** is a property of a member, not a role.

## Reason

The cheap moment to choose a neutral word is now, while three files exist. Option C reads better today and costs the most later, because the ubiquitous language is the one thing in a spec that cannot be renamed quietly.

We chose A over B because permission and care are genuinely two different axes, and collapsing them hides a difference we will need: an organizer is about authority, a minor is about protection. Keeping them separate means a flat share carries no vocabulary it does not use.

The cost of A is real — a spec author can forget the minor case. We accept it because the **By role** section is already a required part of every use case, and the `Minor member` row in that table is what forces the question to be answered. [[users]] also lists the minor questions that are still open, so a reader can see what has not been settled.

"Family" is still the right word in marketing and in the interface. It is not the word in the spec.

## Affects

- [[domain]] — defines household, member, organizer and minor
- [[users]] — one persona per role, plus the open questions about minors
- [[templates/module/use-cases/use-case]] — the **By role** table rows are organizer, member, minor member

## When to revisit

If a household turns out to need more than one level of authority — for example a member who can assign work but cannot remove people — then the permission axis needs a third role and this record should be superseded.
