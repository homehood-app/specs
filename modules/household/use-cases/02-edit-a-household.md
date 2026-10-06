---
status: draft
updated: 2026-10-06
superseded-by:
---

# Edit a household

As the owner, I want to change the household's data so that it describes the home as it is now.

**Actors:** [[users#owner]]

## Pre-conditions

- The household exists
- The actor is its owner

## Main flow

1. The owner changes the household data.
2. The system saves the change.
3. Every member sees the household under its new data.

## Alternative flows

None.

## Exception flows

### The actor is not the owner

1. The system refuses and says only the owner changes the household.
2. Nothing changes.

### The name is emptied

1. The system refuses and asks for a name.
2. Nothing changes.

## Post-conditions

- The household data is what the owner wrote
- Membership and tasks are untouched

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | The household data | Change it |
| Organizer | The household data | Nothing. Running the household is not changing it |
| Member | The household data | Nothing |
| Minor member | The household data | Nothing |

## Applied business rules

- [[rules#only-the-owner-changes-the-household-itself]] — editing the data is the owner's alone
