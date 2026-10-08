# Homehood Specs — Agent Instructions

Read this file before you read or write anything else in this repository.

## What this repository is

The single source of truth for the Homehood product. It captures what the product does, for whom, and the rules that govern its behavior — independent of how it is implemented.

It is not documentation of the code. If the code and the spec disagree, that is a problem to raise with the engineer, not something to fix by editing the spec to match the code.

## Before you write any code

Read, in this order:

1. `overview.md` — what the product is and who it is for
2. `domain.md` — the shared vocabulary; use these words, do not invent synonyms
3. `users.md` — the roles and what each one can and cannot do

Then identify the module the work belongs to and read:

- `modules/{module}/overview.md` — the module's boundaries
- `modules/{module}/domain.md` — concepts specific to the module
- `modules/{module}/rules.md` — the business rules that govern it
- `modules/{module}/use-cases/` — the relevant use cases

If the work touches a behavior that is not in the spec, stop and say so. Do not infer the product rule and build it.

## Structure

### Root level

- `overview.md` — product vision, business model, core value proposition
- `domain.md` — vocabulary and concepts shared across the whole product
- `users.md` — user personas and the authority each one holds

A root file says what is true across the whole product. What a user may do in one area of the product belongs to that area, never to a root file. "Who can create a task" goes in the module's `rules.md` and in the **By role** section of its use cases — not in `users.md`. The same rule applies to `domain.md`: it names a concept; the module says how the concept behaves.

### `modules/{module}/`

Everything relevant to one area of the product:

- `overview.md` — what the module does, its boundaries, what is out of scope, how it relates to other modules
- `domain.md` — concepts that only exist in this module, or that mean something different here
- `rules.md` — business rules that apply across several use cases in this module
- `use-cases/index.md` — list of every use case in the module
- `use-cases/{nn}-{use-case}.md` — one file per use case, numbered in reading order: actor, intent, flows, by role, applied rules

### `decisions/`

Important product decisions: what we decided, when, and why. Append-only. See **Never do** below.

### `templates/`

Always copy the matching template when you create a file.

| Template | Use for |
| --- | --- |
| `templates/module/overview.md` | A new module overview |
| `templates/module/domain.md` | A new module domain file |
| `templates/module/rules.md` | A new rules file |
| `templates/module/use-cases/index.md` | A new use case index |
| `templates/module/use-cases/use-case.md` | A new use case |
| `templates/decision.md` | A new decision record |

## Writing conventions

- File names in kebab-case: `request-payout.md`, not `Request Payout.md`
- Use case file names carry a two-digit order prefix: `01-request-payout.md`. The number gives the reading order within the module. Renumber freely when the order changes
- Dates in ISO format: `YYYY-MM-DD`
- Internal references as wikilinks: `[[note-name]]`, `[[users#organizer]]`
- Use cases reference their applicable rules as wikilinks: `[[rules#rule-name]]`
- Every use case fills the **By role** section. Four rows always: owner, organizer, member, and minor. A minor is not a role — it is a kind of account that always holds the member role — and it keeps a row so the case is answered every time. Add a fifth row, **Guardian**, in any use case where a guardian sees or does something; a guardian is the account responsible for a minor account, and is not a role either. `Nothing.` is a valid cell; blank is not.
- Keep each file focused. A `rules.md` that grows too large means the module should be split.
- Write in English.

## What never goes in this repository

- Implementation details: language, framework, database structure, design patterns
- API contracts
- Infrastructure and deployment
- Implementation status, priority, and sprint planning — those live in the task tracker
- Meeting notes

The test: if it survives a full rewrite of the app, it belongs here. If it changes when the sprint changes, it does not.

## Never do

- Do not write or change any file without explicit instruction from the engineer or the product manager.
- Do not contradict or ignore a rule or use case without explicit confirmation from a human. Raise the conflict instead.
- Do not delete a file without confirmation.
- Do not edit a decision record to change its outcome. Decision records are append-only. To reverse a decision, write a new record, set `supersedes` on the new one and `superseded-by` on the old one.
- Do not invent a product fact to fill a gap. An empty section is honest; a guess is not. Ask.
- Do not change the folder structure without updating this file and `README.md`.

## How changes land

Branch from `main`, edit, open a pull request, and state the problem the change solves. A human merges it. Never commit to `main` directly.
