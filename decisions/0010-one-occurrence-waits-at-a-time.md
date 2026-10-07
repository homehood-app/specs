---
decision: 0010
date: 2026-10-07
status: accepted
supersedes:
superseded-by:
---

# 0010 — One occurrence waits at a time, and a missed one is gone

## Question

Nobody did yesterday's occurrence, and today's is due. Does yesterday's stay open and overdue, or does it go?

## Options

### A — It stays open and overdue

Occurrences collect. Yesterday's dishes task and today's are both waiting.

- **Good:** Nothing is lost. The owner sees the true size of the debt, and a member who falls two days behind can still catch up by doing both.
- **Cost:** A week away leaves seven dishes tasks, and the member who comes back to them is not motivated by the list — they are buried by it. The list stops answering "what do I have to do today", which is the one question a member opens the product for. Worse, the debt is closeable: a member can sit down and close seven identical tasks in a minute, and any future scoring would pay them for work that did not happen seven times.

### B — The new one replaces it, and the routine records a miss

Only one occurrence of a routine waits at a time. An occurrence nobody started is deleted when the next is due, and the routine keeps the fact that the date was missed.

- **Good:** What a member sees today is what they can do today, always, for every routine. The miss is a fact on the routine, so the household can see how a routine is really going without the undone work pretending to be work still available. A miss cannot be closed, so it cannot be collected or scored.
- **Cost:** A member who does the dishes late, the next morning, cannot mark yesterday done — they do today's, and yesterday stays a miss. The record is slightly unfair to the person who caught up, and the household loses the ability to clear a backlog honestly.

## Decision

Option B.

- When a routine makes an occurrence, an earlier occurrence of the same routine still in `Open` is deleted, and the routine records a **miss** for that date
- An earlier occurrence in `Started` is left exactly as it is, and the routine records no miss. The work was begun, so it was not missed
- A `Closed` or `Archived` occurrence is finished. There is nothing to record
- A miss belongs to the routine, not to a task. It cannot be done, closed or undone
- Pausing a routine records no miss for the dates it skips

## Reason

A routine manager must keep today's list true. The moment a member's list holds yesterday's work as well, the list stops being an answer and becomes an archive to sort through, and the household goes back to asking each other what is still outstanding.

The second argument is that undone work should not be able to pretend to be available work. Under Option A, six stale dishes tasks are indistinguishable from six real ones, and closing them is indistinguishable from doing them. The product's whole claim is that closed means done. Keeping the miss on the routine, where it cannot be closed, protects that claim — and it closes the obvious way to farm a future scoring system before the scoring exists.

The rule that a `Started` occurrence survives comes straight from [[0005-an-active-task-of-a-former-member-waits]] and from [[modules/tasks/rules#archiving-ends-a-task-that-was-started]]: work somebody began is a record, and records are not deleted. Nothing in this decision ever deletes something a member touched.

We accept the cost. The member who does yesterday's dishes this morning is recorded as having missed yesterday. If that turns out to sting in real households, the fix is to let a miss be answered, not to let occurrences pile up.

## Affects

- [[modules/routine/rules#a-routine-never-has-two-occurrences-waiting]]
- [[modules/routine/domain]] — the **miss** concept
- [[modules/routine/use-cases/05-miss-an-occurrence]]
- [[modules/routine/use-cases/08-end-a-routine]] — ending a routine deletes its waiting occurrence for the same reason
- [[modules/tasks/rules#who-can-end-a-task]] — a routine deletes its own waiting occurrence
- [[0009-an-occurrence-appears-on-the-calendar]] — a miss needs a date on which the work was expected

## When to revisit

If members tell us the miss is unfair when they caught up a day late, the answer is a way to answer a miss on the routine — not a backlog of open tasks. Revisit this record when scoring is specified, because scoring is the thing that makes a miss carry weight.
