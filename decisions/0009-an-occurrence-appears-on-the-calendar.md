---
decision: 0009
date: 2026-10-07
status: accepted
supersedes:
superseded-by:
---

# 0009 — An occurrence appears on the calendar, not after the last one closes

## Question

A routine makes an occurrence. When does the next one appear: on the date the schedule gives, or a period after somebody closed the one before?

## Options

### A — On the calendar

Tuesday's occurrence appears on Tuesday, whatever happened to Monday's.

- **Good:** The household can trust the plan. "Bins on Thursday" means there is a bins task on Thursday, every week, and a member who opens the product sees the true shape of their week. A routine nobody does still asks, which is how the household finds out that it is not being done.
- **Cost:** It asks for work that may not make sense — a daily routine keeps asking while the household is away. Work measured from the last time it was done is expressed badly: "wash the car every two weeks" becomes a fixed fortnightly date rather than two weeks after the last wash.

### B — A period after the last one closes

The next occurrence appears *n* days after the executor closed the one before.

- **Good:** Right for work whose clock starts when you finish: the sheets, the car, the filter. No occurrence is ever pointless, because each one follows a real completion.
- **Cost:** A routine nobody does stops for ever, in silence. One member who never closes Monday's dishes makes the dishes disappear from the household — the routine manager quietly stops managing. There is also no answer to "what is due on Thursday", because nothing is due until something is finished.

## Decision

Option A. An `Active` routine makes one occurrence for every date its schedule gives, on that date, whatever happened to the occurrence before it.

- The first occurrence is on the routine's start date
- A `Paused` or `Ended` routine makes none
- A monthly routine set to a date the month does not have makes its occurrence on the last day of that month

## Reason

The failure mode decides it. Under Option A the household is asked for something it does not need, notices, and ignores or pauses the routine. Under Option B the household is not asked at all and does not notice — the routine fails by going quiet, which is exactly the failure Homehood exists to prevent. A silent failure in a product whose job is "is it done?" is worse than a noisy one.

Option A also makes [[0010-one-occurrence-waits-at-a-time]] possible. A miss only means something when there was a date on which the work was expected. Under Option B nothing is ever missed, because nothing is ever due.

The cost is real and we accept it: Homehood expresses "every two weeks from the last time" badly today. The household's answer is to pause the routine, or to use an ordinary task.

## Affects

- [[modules/routine/rules#an-occurrence-appears-on-its-due-date]]
- [[modules/routine/domain]] — the **schedule** and **due date** concepts
- [[modules/routine/use-cases/05-miss-an-occurrence]] — a miss needs a date on which the work was expected
- [[modules/routine/use-cases/07-pause-and-resume-a-routine]] — the pause is how the household answers the cost

## When to revisit

If households keep asking for "a fortnight after the last wash", the answer is a second kind of schedule next to the calendar one, not a replacement for it. This record should be superseded rather than edited.
