---
status: draft
updated: 2026-10-07
superseded-by:
---

# Set a rotation on a routine

As the owner or an organizer, I want a routine to pass between members in turn so that nobody has to settle whose turn it is.

**Actors:** [[users#owner]], [[users#organizer]]

## Pre-conditions

- The actor is the owner or an organizer of the household
- Every member they put in the rotation is a member of the household

## Main flow

1. The owner or organizer puts two or more members in the rotation, in the order they will take their turns.
2. The system replaces the routine's single executor with the rotation.
3. The next occurrence goes to the first member in the list.
4. Each occurrence after that goes to the next member down the list. After the last member, the list starts again at the top.

## Alternative flows

### The rotation is set when the routine is created

1. The owner or organizer sets the rotation instead of choosing a single executor, in the same step as [[02-create-a-routine-for-another-member]].

### A member is removed from the rotation

1. The system takes them out of the list and keeps the order of the rest.
2. The turn carries on from the member whose turn it was, or from the next one down if it was the removed member's turn.
3. The occurrences the removed member already did still name them. The record is not rewritten.

### The rotation goes back to a single executor

1. The owner or organizer names one member as the executor.
2. The rotation is gone, and the turn never moves again.

## Exception flows

### The actor is a member or a minor member

1. The system refuses and says only the owner and an organizer can set a rotation.
2. Nothing changes. A rotation names other members, so it needs organizer authority.

### The rotation holds fewer than two members

1. The system refuses and says a rotation needs at least two members.
2. Nothing changes. A routine with one member in it has a single executor instead.

### An organizer puts the owner in the rotation

1. The system refuses and says an organizer cannot act on the owner's work.
2. Nothing changes. The owner puts themselves in a rotation.

### A chosen member is not a member of the household

1. The system refuses and says the person is not in this household.
2. Nothing changes.

## Post-conditions

- The routine holds a rotation of two or more members and no single executor
- Every member in the rotation can see the routine
- A member in the rotation sees only the occurrences that fell to them
- The turn moves one place every time an occurrence is made

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | Every routine in the household, and whose turn is next | Set, change and clear the rotation of any routine, and put themselves in it |
| Organizer | Every routine in the household, and whose turn is next | Set, change and clear the rotation of any routine that does not name the owner |
| Member | The routines they are in the rotation of, and whose turn is next on those | Nothing. A member cannot change a rotation, not even one they are in |
| Minor member | The routines they are in the rotation of, and whose turn is next on those | Nothing. A minor cannot change a rotation, not even one they are in |

## Applied business rules

- [[rules#the-executor-of-an-occurrence-is-whoevers-turn-it-is]] — one executor or a rotation, never both, and how the turn moves
- [[rules#a-member-sets-a-routine-for-themselves-naming-another-member-needs-authority]] — a rotation names other members, so it needs authority
- [[rules#an-organizer-cannot-act-on-the-owners-routines]] — an organizer cannot put the owner in a rotation or take them out
- [[rules#a-routine-is-visible-to-the-people-its-occurrences-are-visible-to]] — everybody in the rotation sees the routine
