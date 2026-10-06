# Homehood Specs

This repository is the single source of truth for the Homehood product. It says what the product does, for whom, and the rules that govern its behavior. It does not say how the product is built.

Humans and AI agents both read it. Keeping it accurate is the team's responsibility, not the agent's. Agents start at [[AGENTS]].

The structure follows [SDAD](https://github.com/TiagoDamascena/sdad) (Spec-Driven Agentic Development). We did not invent a second standard. We adopted the SDAD reference layout and added two things: a `decisions/` directory for important product decisions, and a required **By role** section in every use case.

## What belongs here

**Belongs here:**

- Business rules and constraints
- Use cases and user interactions
- Domain concepts and vocabulary
- User personas and profiles
- Important product decisions: what we decided, why, and when
- Images and diagrams that the specs reference

**Does not belong here:**

- Implementation details: language, framework, database structure, design patterns
- API contracts
- Infrastructure and deployment
- Implementation status, priority, and sprint planning — those live in the task tracker
- Meeting notes

**The test:** if it survives a full rewrite of the app, it belongs here. If it changes when the sprint changes, it does not.

## Structure

```
.
├── README.md
├── AGENTS.md            # Instructions for AI agents working in this repository
├── overview.md          # What the product is, its purpose and business model
├── domain.md            # Shared vocabulary and concepts across the product
├── users.md             # User personas and profiles
├── modules/
│   └── {module}/
│       ├── overview.md  # What this module does and its boundaries
│       ├── domain.md    # Concepts specific to this module
│       ├── rules.md     # Business rules that govern this module
│       └── use-cases/
│           ├── index.md # List of all use cases in this module
│           └── {nn}-{use-case}.md
├── decisions/
│   ├── index.md         # List of all product decisions, newest first
│   └── {nnnn}-{slug}.md
├── assets/              # Images and other files the specs reference
└── templates/           # Templates for new files
```

## Modules

A module is a cohesive area of the product with clear boundaries. Good modules map to how the business thinks about the product, not to how the code is structured.

If you are not sure whether an area deserves its own module, ask: can you explain this area on its own to someone who knows nothing about the rest of the product? If yes, it is a module.

## Use cases: the By role section

Every use case must fill a **By role** section saying what an owner, an organizer, a member and a minor member each see and can do.

It is required because Homehood is a product with several roles in one household, and we get the roles wrong by default when the section is optional.

### Use case status

A use case carries a `status` field in its frontmatter. It describes the *document*, not the code:

| `status` | Meaning |
| --- | --- |
| `draft` | Written, not yet agreed |
| `approved` | Agreed by the team |
| `superseded` | Replaced by another use case; `superseded-by` names it |

Whether the use case is built, and when it will be, belongs in the task tracker — not here.

## Decisions

A spec says what is true now. A decision record says what we decided about the product, when, and why — and what we rejected.

Record a decision when the choice shapes the product and someone will ask "why is it like this?" later. A rule that is simply true goes in `rules.md`; the argument behind it goes here.

Decision records are **append-only**. Never edit a record to change the outcome. To reverse a decision, write a new record, set `supersedes` on the new record, and set `superseded-by` on the old one.

Numbers are sequential and never reused: `0005-minors-cannot-delete-a-task.md`.

## Workflow

### Write or change a spec

1. Create a branch from `main`.
2. Add or edit the Markdown files. Copy from `templates/`.
3. If the change settles an important product question, add a decision record.
4. Open a pull request. State the problem the change solves.

### Review a spec

- Make sure every requirement can be tested.
- Make sure the **By role** section is filled, with a row per role.
- Ask questions in the pull request comments.
- Merge when the team agrees.

## Conventions

- File names in kebab-case: `auth-flow.md`, not `Auth Flow.md`
- Use case file names carry a two-digit order prefix: `01-create-a-household.md`. The number is the order a reader should meet them, not the order they were written. Numbers are renumbered freely when the order changes, because nothing outside the module links to them
- Dates in ISO format: `YYYY-MM-DD`
- Internal links as wikilinks: `[[users#organizer]]`
- Keep each file focused. A `rules.md` that grows too large is a signal to split the module.
- Write in English.

## Reading the specs

The specs are Markdown files with wikilinks. [Obsidian](https://obsidian.md) renders the links and the graph. Open this repository as a vault.
