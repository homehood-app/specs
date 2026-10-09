---
status: draft
updated: 2026-10-08
superseded-by:
---

# Delete a minor account

As the guardian of a minor account, I want to delete it so that an account nobody needs any more stops existing.

**Actors:** [[users#guardian]]

## Pre-conditions

- The minor account exists
- The actor is its guardian

## Main flow

1. The guardian asks to delete the account.
2. The system says how many households the account is a member of, and warns that the child loses access to all of them and that this cannot be undone.
3. The guardian confirms.
4. The system deletes the account and ends every membership it held.
5. In each of those households, the child is now a former member. What they did there stays on the record.

## Alternative flows

### The account belongs to no household

1. Step 2 says there is nothing to lose access to.
2. The rest is the same.

### The account is on active tasks

1. Those tasks become unresolved in their household, and wait for a member with organizer authority there. See [[tasks/use-cases/08-resolve-a-former-members-tasks]].
2. The guardian does not choose where any of that work goes, and is not shown it. A guardian who is not a member of the household cannot see inside it.
3. The system tells the guardian that each household will have work to settle, without saying what it is.

### The guardian wants the child to keep what they did

1. Deleting is the wrong act. The guardian makes the account a full account instead, and the child keeps everything. See [[04-make-a-minor-account-a-full-account]].

## Exception flows

### The actor is not the guardian

1. The system refuses. Nobody but the guardian deletes a minor account — not an owner of a household the child is in, not an organizer, not the child.
2. Nothing changes.

### The guardian wants to delete their own full account instead

1. Out of scope. How a full account is deleted is not specified yet.
2. What is settled is that a guardian cannot leave a minor account behind: every one they hold is handed on or deleted first. See [[rules#every-minor-account-has-exactly-one-guardian]].

## Post-conditions

- The minor account no longer exists, and nobody can sign in to it
- The child is a former member of every household the account belonged to
- Every closed and archived task still names them, and every comment they wrote is unchanged
- Every `Open` and `Started` task they were on is unresolved, and waiting in its own household
- Each of those households still has exactly one owner
- Nothing is recoverable

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | That the member is gone, and the work they left waiting | Nothing. The owner cannot delete a child's account, and is not asked before it happens |
| Organizer | That the member is gone, and the work they left waiting | Nothing. Resolve the waiting work afterwards, as for any former member |
| Member | That the person is no longer in the household | Nothing |
| Minor | Nothing of this use case, until they cannot sign in | Nothing. A child cannot delete their own account, and cannot stop it being deleted |
| Guardian | The minor accounts they hold, and how many households each one belongs to | Delete a minor account they hold |

## Applied business rules

- [[rules#only-the-guardian-ends-a-minor-account]] — deletion is the guardian's alone, and it is the only way the account ends
- [[rules#a-guardian-decides-the-account-not-the-household]] — the guardian ends the memberships without seeing inside any of those households
- [[household/rules#a-former-member-stays-on-what-they-left-behind]] — each household keeps the record of what the child did there
- [[household/rules#an-active-task-of-a-former-member-waits-for-organizer-authority]] — the household settles the work, not the guardian
