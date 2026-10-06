---
decision: 0002
date: 2026-10-06
status: accepted
supersedes:
superseded-by:
---

# 0002 — Implementation status and priority live on the board

## Question

Where do we record whether a spec is built, and which spec is next?

## Options

### A — The Paperclip board only

- **Good:** The repository can never go stale. No double bookkeeping.
- **Cost:** You cannot read "what is built" from a `git clone` alone.

### B — The repository: a `ROADMAP.md` plus a status field in each spec

- **Good:** Everything offline and everything diffable.
- **Cost:** Two places to update per change. It will drift, and then the repository lies.

### C — The board is the source, and a job writes a `STATUS.md` mirror into the repository

- **Good:** Both benefits at once.
- **Cost:** Automation to build and keep alive. Not worth it below roughly twenty specs.

## Decision

Option A. The Paperclip board is the only source of truth for implementation status and priority.

## Reason

Status and priority change every week. Specs change rarely. Putting weekly state into a repository of rarely-changing documents guarantees drift, and a stale status field is worse than no status field: readers trust it and act on it.

SDAD's own principle is that the spec and the implementation are always in sync. The way to honor that is to keep the repository free of anything that goes out of sync.

Option C is the right end state. It is not worth the automation at two specs.

## Consequences

- No `ROADMAP.md` and no status dashboard in this repository.
- A use case file carries a `status` field, but it describes the *document*, not the code: `draft`, `approved`, or `superseded`.
- A use case file may carry a `task` field linking to the Paperclip task, once work on it starts. The link points at the board; the state stays there.
- To answer "what is built", read the board.

## When to revisit

When the repository passes roughly twenty use cases, or when someone needs to answer "what is built" without board access. Then move to option C.
