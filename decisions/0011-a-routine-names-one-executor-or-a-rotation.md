---
decision: 0011
date: 2026-10-07
status: accepted
supersedes:
superseded-by:
---

# 0011 — A routine names one executor or a rotation

## Question

Does the same member do a routine every time, or does it pass between members in turn?

## Options

### A — Always one executor

A routine names one member. A household that shares the work writes one routine for each of them.

- **Good:** The smallest module. One executor is one rule, and every occurrence goes to the obvious person.
- **Cost:** The household cannot say "we share the dishes". It has to fake it with several routines on different days and keep them in step by hand, and every change — somebody is away, somebody swaps — means editing them all. The product leaves the household's commonest recurring argument untouched.

### B — One executor, or a rotation

A routine names one member, or holds an ordered list of two or more who take it in turn.

- **Good:** It answers "whose turn is it", which is the weekly form of "who is responsible for this" — the question [[overview]] says the product exists for. One routine describes shared work, and the turn is a fact rather than an opinion.
- **Cost:** A second shape for every rule about the executor, and a new thing to keep track of: the turn. More to specify, and more for the household to understand.

### C — Always a rotation

Every routine holds a list. A routine for one member holds a list of one.

- **Good:** One shape, one rule, no branch.
- **Cost:** "This is always mine" is the commonest case and it is expressed as a degenerate list. The member has to understand rotations to say the simple thing.

## Decision

Option B. A routine names exactly one executor, or holds a rotation of two or more members. Never both, and never none.

- With one executor, every occurrence goes to them and the turn never moves
- With a rotation, each occurrence goes to the next member down the list, and the list starts again at the top
- **The turn moves when the occurrence is made, not when it is closed.** A missed occurrence does not give a member a second turn
- Taking a member out of a rotation keeps the order of the rest, and does not rewrite the turns already taken

## Reason

[[overview]] says Homehood ends two arguments: nobody knew it was theirs, and nobody knew it was finished. For recurring work, "nobody knew it was theirs" *is* "it was not my turn". A routine manager that cannot hold a turn solves the single-task version of the problem and leaves the recurring version — the one that happens every week — to the household.

Option C was rejected because it makes the simple case pay for the shared case. Most routines belong to one person.

The sub-question worth recording is when the turn moves. The rejected alternative is that a missed occurrence keeps your turn, so the member who skipped is asked again until they do it. It is more obviously fair, and we rejected it for two reasons. It punishes the rest of the rotation, who now wait on one member before the routine comes back round to them — the work stops moving because somebody stopped. And it fights [[0010-one-occurrence-waits-at-a-time]], which exists so that a missed date is over. A turn that is still owed is a missed date that is not over. The miss is recorded on the routine instead, so the household can see who is not taking their turns without the routine stalling on them.

## Affects

- [[modules/routine/rules#the-executor-of-an-occurrence-is-whoevers-turn-it-is]]
- [[modules/routine/domain]] — the **rotation** and **turn** concepts
- [[modules/routine/use-cases/03-set-a-rotation-on-a-routine]]
- [[modules/routine/rules#a-routine-is-visible-to-the-people-its-occurrences-are-visible-to]] — everybody in a rotation sees the routine, and only their own occurrences
- [[0012-a-routine-for-another-member-needs-organizer-authority]] — a rotation names other members, so setting one needs authority

## When to revisit

If households ask to swap a single turn without changing the list — "I am away on Thursday, you take mine" — that is a real gap and this record should be extended by a new one. Nothing here allows it today.
