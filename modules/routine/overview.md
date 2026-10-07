# Routine

The recurring part of the household's work. A routine is a standing instruction — "the dishes, every day, Lucy" — and it makes one ordinary task each time the work comes round.

Homehood is a routine manager. This is the module that earns the name. Without it the household writes the same task again every morning.

## Actors

- [[users#owner]] — sees every routine in the household, and can act on any of them
- [[users#organizer]] — sees every routine in the household, and can act on any whose executor is not the owner
- [[users#member]] — sets a routine for themselves, does the routines set for them, and sees only the routines that concern them
- [[users#minor-member]] — a member under the care of the household

## Responsibilities

- What a routine is, and what it holds: the work, the schedule and who does it
- Making an occurrence of a routine, and when
- What happens to an occurrence nobody did
- Who the executor of an occurrence is, including a rotation that moves turn by turn
- Who can set a routine, change it, pause it and end it
- What happens to a routine when a member on it leaves the household
- Who can see which routines

## Out of scope

- Everything an occurrence does once it exists. An occurrence is an ordinary task, and [[tasks/overview]] owns it. This module adds no task state and changes no task rule
- A time of day. A routine is due on a date, not at an hour
- An end date set in advance. A routine runs until somebody pauses or ends it
- Reminders and notifications. Nothing here says the household is told anything
- Scoring and points. The product has no scoring concept yet. The rule that a missed occurrence cannot be done later was chosen partly so that a future scoring system cannot be farmed — see [[decisions/0010-one-occurrence-waits-at-a-time]]
- What a minor sees less of. Nothing in this module narrows what a minor sees. The open question stays where [[users]] leaves it

## Related modules

- [[tasks/overview]] — a routine makes tasks, and the tasks module governs every one of them from the moment it exists
- [[household/overview]] — a routine belongs to one household, and everybody it names is a member of it

## Use cases

[[use-cases/index]]

## Business rules

[[rules]]
