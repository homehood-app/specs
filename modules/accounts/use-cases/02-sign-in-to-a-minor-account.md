---
status: draft
updated: 2026-10-08
superseded-by:
---

# Sign in to a minor account

As a child, I want to reach my own account so that I can do my part of the household's work myself.

**Actors:** [[users#minor]], [[users#guardian]]

## Pre-conditions

- The minor account exists
- The child has been given its handle, and a claim code if the account is not claimed yet

## Main flow

1. The child gives the account's **handle** and their **PIN**.
2. The system signs the child in to the account.
3. The child sees every household the account is a member of, and their own work in each one, exactly as any member does.

## Alternative flows

### The child has not claimed the account yet

1. The child gives the handle and the **claim code** their guardian gave them.
2. The system asks the child to set a **PIN**, and the child sets one.
3. The claim code stops working. It is used once.
4. The child is signed in. From now on the handle and the PIN are the way in.
5. The guardian sees that the account has been claimed.

### The child signs in on a device they already used

1. The account stays reachable on that device until somebody signs out of it. The child does not type the handle every day.
2. A shared tablet can hold more than one account this way. Each child gives their own PIN.

### The child changes their PIN

1. The child gives the PIN they have, then the new one.
2. The guardian is not told the new PIN, and never sees it.

### The child wants a different name or handle

1. The child cannot change either. Their guardian does — see [[rules#an-account-holds-a-name-a-handle-and-a-picture]].
2. The child can change their picture.

### The child cannot sign in any more

1. The child tells their guardian. The guardian issues a new claim code.
2. The new claim code clears the PIN. Nothing else about the account changes: every membership, every task and every comment stays.
3. The child claims the account again and sets a new PIN, as in **The child has not claimed the account yet**.
4. This is the only reset, and the only recovery. A guardian can clear a PIN and can never set one.

### The guardian wants to know whether the child can get in

1. The guardian sees, for each minor account they hold: whether it has been claimed, when it was last signed in to, and whether a claim code is waiting.
2. The guardian does not see the PIN.

### The account belongs to no household

1. The child signs in the same way and sees no household and no work. The account is theirs to reach whether or not anybody has invited them.

## Exception flows

### The PIN is wrong

1. The system refuses and does not say whether the handle exists.
2. After too many wrong tries the account stops accepting the PIN. Only a new claim code from the guardian opens it again, and the guardian is told that it happened.

### The claim code has expired, or was already used

1. The system refuses. A claim code is used once and does not last.
2. The guardian issues another one.

### The handle does not exist

1. The system refuses, and says the same thing it says for a wrong PIN. It does not confirm whether a handle belongs to anybody.

### Somebody tries to sign in to a minor account with an email address and a password

1. The system refuses. A minor account holds neither — see [[domain#account]].
2. Once the account has become a full account, the opposite is true: the handle and the PIN stop working — see [[05-finish-becoming-a-full-account]].

### The guardian tries to sign in to the minor account

1. A guardian signs in to their own account, not to the child's. Guardianship is not a way in.
2. A guardian who clears the PIN can of course reach the account afterwards, by setting one in the child's place. That is a known cost, and the guardian can already delete the account — see [[decisions/0014-a-child-signs-in-with-a-handle-and-a-pin]].

## Post-conditions

- The child is signed in to their own account, on any device they chose
- The account has a PIN that only the child knows
- Any claim code that was outstanding is spent
- The guardian can tell that the child reached the account, and when they were last there

## By role

Signing in happens outside every household, so no household role has anything to do here. The minor row is the use case.

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | That a minor who is a member of their household has not reached their account yet, nothing more. Not the handle, not whether a code is waiting | Nothing. The owner cannot issue a way in to an account they do not hold, and cannot reset a child's PIN |
| Organizer | The same as the owner | Nothing |
| Member | Nothing of this use case | Nothing |
| Minor | Their own households and their own work, once they are in | Claim the account with a claim code, set a PIN, sign in with the handle and the PIN, change their PIN, change their picture |
| Guardian | For each minor account they hold: whether it is claimed, when it was last signed in to, whether a code is waiting, and that wrong tries stopped it. Never the PIN | Issue a claim code, which clears the PIN. Change the name, the handle and the picture |

## Applied business rules

- [[rules#a-guardian-issues-the-way-in-and-can-issue-it-again]] — the whole of this use case rests on it
- [[rules#an-account-holds-a-name-a-handle-and-a-picture]] — what the child may change, and what they may not
- [[rules#a-guardian-decides-the-account-not-the-household]] — a household cannot let a child in, and a guardian signs in to nothing
- [[household/rules#a-minor-is-a-member-and-stays-a-member]] — what the child finds once they are in is a plain member's view
