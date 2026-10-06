---
status: draft
updated: 2026-10-06
superseded-by:
---

# Create a household

As a person with no household, I want to create one so that I can start coordinating the home's routine.

**Actors:** [[users#organizer]]

## Pre-conditions

- The person has an account

## Main flow

1. The person gives the household a name.
2. The system creates the household.
3. The system makes the person a member of it, and an organizer.

## Alternative flows

### The person already belongs to a household

1. The system creates the new household anyway.
2. The person is a member of both. Each household is a separate boundary.

## Exception flows

### The name is empty

1. The system refuses and asks for a name.
2. No household is created.

## Post-conditions

- The household exists
- The person is its member and its only organizer
- The household has no tasks

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Organizer | The household they just created, empty | Create a household, and become its first organizer |
| Member | Nothing. There is no household to be a member of yet | Nothing |
| Minor member | Nothing. There is no household to be a member of yet | Nothing |

## Applied business rules

- [[rules#a-household-always-has-an-organizer]] — the creator becomes the first organizer, so the rule holds from the start
