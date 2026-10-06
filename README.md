# Homehood Specs

This repository is the single source of truth for the Homehood product. It says what the product does, for whom, and the rules that govern its behavior. It does not say how the product is built.

Humans and AI agents both read it. Keeping it accurate is the team's responsibility, not the agent's.

The structure follows [SDAD](https://github.com/TiagoDamascena/sdad) (Spec-Driven Agentic Development). We did not invent a second standard. We adopted the SDAD reference layout and added three things it leaves open: a home for decisions, a rule for where implementation status lives, and two required sections in every use case. See [[decisions/index]].

## What belongs here

**Belongs here:**

- Business rules and constraints
- Use cases and user interactions
- Domain concepts and vocabulary
- User personas and profiles
- Decisions about the specs, and the reason for each one
- Images and diagrams that the specs reference

**Does not belong here:**

- Implementation details: language, framework, database structure, design patterns
- API contracts
- Infrastructure and deployment
- Dated roadmaps and sprint plans
- Meeting notes
- Status dashboards

**The test:** if it survives a full rewrite of the app, it belongs here. If it changes when the sprint changes, it does not.

## Where implementation status and priority live

**On the Paperclip board. Not in this repository.**

Status and priority change every week. Specs change rarely. If weekly state lives here, the repository starts to lie. The board is the only source of truth for what is built, what is next, and what is paused. See [[decisions/0002-implementation-status-lives-on-the-board]].

A use case file carries one `status` field, but it describes the *document*, not the code:

| `status` | Meaning |
| --- | --- |
| `draft` | Written, not yet agreed |
| `approved` | Agreed by the board |
| `superseded` | Replaced by another use case; `superseded-by` names it |

## Structure

```
.
├── README.md
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
│           └── {use-case}.md
├── decisions/
│   ├── index.md         # List of all decisions, newest first
│   └── {nnnn}-{slug}.md
├── assets/              # Images and other files the specs reference
└── templates/           # Templates for new files
```

## Modules

A module is a cohesive area of the product with clear boundaries. Good modules map to how the business thinks about the product, not to how the code is structured.

If you are not sure whether an area deserves its own module, ask: can you explain this area on its own to someone who knows nothing about the rest of the product? If yes, it is a module.

## Use cases: two required sections

Every use case must fill these two sections. They are required because Homehood gets them wrong by default when they are optional.

**By role.** What a parent, a child, and another member each see and can do. If the behavior changes with the child's age, split the row and name the age band.

**Gamification.** What earns points, what a user can game, and what feels fair. If the use case has no gamification, write `None.` — that is a decision, not an empty field.

## Decisions

A spec says what is true now. A decision record says why we got there and what we rejected.

Decision records are **append-only**. Never edit a decision to change the outcome. To reverse a decision, write a new record, set `supersedes` on the new record, and set `superseded-by` on the old one.

Numbers are sequential and never reused: `0003-child-sees-sibling-points.md`.

## Workflow

### Write or change a spec

1. Create a branch from `main`.
2. Add or edit the Markdown files. Copy from `templates/`.
3. If the change settles an open question, add a decision record.
4. Open a pull request. State the problem the change solves.

### Review a spec

- Make sure every requirement can be tested.
- Make sure the **By role** and **Gamification** sections are filled.
- Ask questions in the pull request comments.
- Merge when the team agrees.

## Conventions

- File names in kebab-case: `auth-flow.md`, not `Auth Flow.md`
- Dates in ISO format: `YYYY-MM-DD`
- Internal links as wikilinks: `[[users#parent]]`
- Keep each file focused. A `rules.md` that grows too large is a signal to split the module.
- Write in English.

## Reading the specs

The specs are Markdown files with wikilinks. [Obsidian](https://obsidian.md) renders the links and the graph. Open this repository as a vault.
