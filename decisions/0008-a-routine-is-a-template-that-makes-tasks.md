---
decision: 0008
date: 2026-10-07
status: accepted
supersedes:
superseded-by:
---

# 0008 — A routine is a template that makes tasks

## Question

Homehood is a routine manager, and [[domain]] named *routine* without saying how recurrence works. Is a routine a separate thing that makes tasks, or is it a setting on a task that makes the task come back?

Every other answer about recurrence depends on this one.

## Options

### A — A routine is a template, and each turn is its own task

The routine holds the work, the schedule and the executor. It makes one ordinary task for each date.

- **Good:** Every date has its own record. The household can see that the dishes were done on Monday, missed on Tuesday and done by somebody else on Wednesday, with the comments from each day attached to that day. The tasks module does not change: `Closed` stays final, a task still moves in one direction, and no new task state is needed.
- **Cost:** Two things to understand instead of one — the routine and the tasks it makes. The household sees a list of routines as well as a list of tasks, and has to learn that ending a routine is not the same as closing today's task.

### B — Recurrence is a setting on a task

The task carries "every day". When the executor closes it, it opens again with a new date.

- **Good:** One concept. Nothing new to learn, and no second list.
- **Cost:** One row of history for work that happened a hundred times. Nobody can answer "who did this last Tuesday", because last Tuesday was overwritten. `Closed` stops being final, which contradicts [[modules/tasks/rules#a-task-moves-in-one-direction]]. Comments pile onto one task across months. A missed day leaves no trace at all, because there was never a task for it.

## Decision

Option A. A routine is a template. It holds the work, the schedule and who does it, and it makes one ordinary task — an **occurrence** — for each date its schedule gives.

- A routine is never started and never closed. It is `Active`, `Paused` or `Ended`
- An occurrence is a task, with nothing special about it. [[modules/tasks/rules]] governs it entirely
- This module adds no task state and changes no task rule

## Reason

The product exists to answer "who is responsible for this, and is it done?" For recurring work the useful form of that question is dated: who did it *yesterday*, and was it done *this week*. Option B cannot answer a dated question, because it keeps one row.

The second reason is that Option B breaks a rule the team already settled. `Closed` is final and a task moves in one direction. A recurring task that reopens itself makes `Closed` a stage rather than an end, and every rule written on top of that — archiving, deleting, resolving a former member's tasks — has to be re-read with an exception in it.

Option A costs the household one extra concept. That is a real cost, and it is the smaller one.

## Affects

- [[domain]] — the **routine** concept, which no longer says that recurrence is unspecified
- [[modules/routine/overview]] and [[modules/routine/domain]] — the whole module rests on this
- [[modules/routine/rules#a-routine-makes-tasks-and-is-never-one]]
- [[modules/tasks/overview]] — recurrence left the **Out of scope** list in the same change
- [[modules/routine/use-cases/04-do-an-occurrence-of-a-routine]] — the bridge between a routine and a task

## When to revisit

If households tell us they only ever want one dishes task and never look at the history, the simpler model is worth reconsidering. Nothing we know now points that way: the record is the product.
