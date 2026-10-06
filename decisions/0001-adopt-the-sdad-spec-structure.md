---
decision: 0001
date: 2026-10-06
status: accepted
supersedes:
superseded-by:
---

# 0001 — Adopt the SDAD spec structure

## Question

The specs repository held only a `README.md`. What structure and templates should Homehood specs follow?

## Options

### A — Adopt the SDAD reference layout as-is

- **Good:** The standard already exists, is written down, and is tested. Agents and humans read the same layout. Nothing to invent and nothing to maintain.
- **Cost:** SDAD leaves three things open: a home for decisions, a rule for where implementation status lives, and role and gamification coverage inside a use case.

### B — Design a Homehood-specific structure

- **Good:** Shaped exactly to Homehood from day one.
- **Cost:** A second standard to write, explain, and keep. It would look like SDAD anyway, because SDAD already answers most of it.

### C — Keep one flat Markdown file per spec, as the old README described

- **Good:** No structure to learn.
- **Cost:** No shared vocabulary, no module boundaries, no way to find the rule that governs a behavior. It stops working at around ten specs.

## Decision

Option A. Adopt the SDAD reference layout as-is, and fill only the gaps it leaves open.

## Reason

SDAD is the team's own prior work, so the cost of adoption is close to zero and the team already agrees with its principles. Inventing a parallel standard would produce something very similar with none of that benefit.

The gaps are small and specific, so we close them with additions rather than with a fork:

- A `decisions/` directory, because a spec says what is true now and has no place to say why.
- Implementation status and priority stay on the Paperclip board. See [[0002-implementation-status-lives-on-the-board]].
- Two required sections in every use case, **By role** and **Gamification**, because Homehood gets both wrong by default when they are optional. A family product with several roles and a points system needs each use case to state what a parent, a child, and another member each see, and what a user can game.

## Consequences

- The repository root holds `overview.md`, `domain.md`, `users.md`, `modules/`, `decisions/`, `assets/`, and `templates/`.
- Technical plans, API contracts, database structure, infrastructure, dated roadmaps, and meeting notes do not go in this repository.
- Obsidian is the reader. Internal links are wikilinks.
- The root files `overview.md`, `domain.md`, and `users.md` ship as placeholders. Filling them with real Homehood content is the next piece of work.

## When to revisit

If SDAD changes its reference layout, or if the **By role** and **Gamification** sections turn out to be noise rather than signal after roughly ten use cases.
