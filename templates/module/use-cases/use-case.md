---
status: draft
updated: {{YYYY-MM-DD}}
superseded-by:
---

# {{Title}}

As {{actor}}, I want {{action}} so that {{outcome}}.

**Actors:** [[users#actor-name]]

## Pre-conditions

-

## Main flow

1.

## Alternative flows

### {{Alternative name}}

1.

## Exception flows

### {{Exception name}}

1.

## Post-conditions

-

## By role

Required. Four rows, always: the three roles, and a minor. Minor is not a role — it is a kind of account that always holds the member role — and it keeps a row so that the minor case is answered in every use case instead of remembered. Where a minor behaves exactly as a member, say so; do not leave the row out. Never split a row by age: nothing about a minor depends on an age, because the product holds none. Write `Nothing.` where a role has no view and no action.

Add the fifth row, **Guardian**, when a guardian sees or does something in this use case, and delete it when they do not. A guardian is the one account responsible for a minor account, from outside every household.

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | | |
| Organizer | | |
| Member | | |
| Minor | | |
| Guardian | | |

## Applied business rules

- [[rules#rule-name]] — brief description of why it applies here
