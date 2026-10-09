---
decision: 0014
date: 2026-10-08
status: accepted
supersedes:
superseded-by:
---

# 0014 — A child signs in with a handle and a PIN, and the guardian issues the first way in

## Question

[[0006-a-minor-is-an-account-kind-not-a-household-role]] put the difference about a child on the account and named the person responsible for it, and then left the two doors shut: how a minor account is created, and how a child reaches it. A minor account holds no email address and no password of the usual kind, so neither door can be the ordinary one.

The hard half is the second. A child has to get into the app, in a home that may own one shared tablet and in a home where the child has their own phone, and in both homes at once when the child's parents are separated. Whatever we choose is also the thing the child must do to finish becoming a full account one day, because that is the one act [[0007-no-age-and-one-way-to-a-full-account]] says cannot happen without them.

## Options

### A — The guardian hands the session over

No child sign-in. The guardian opens the app on their own account and changes to the child.

- **Good:** Nothing to build and nothing for a child to remember. No secret held by a six-year-old. The guardian is already trusted with the account, so nothing is weakened.
- **Cost:** It contradicts what a minor is. [[0006-a-minor-is-an-account-kind-not-a-household-role]] says a minor is a plain member who does a member's work in full; a member who can only be let in by somebody else does not run their own part of the household, they are a puppet of it. It breaks completely for a child in two homes, because the guardian may be a member of neither. And it leaves [[0007-no-age-and-one-way-to-a-full-account]] with no way to keep its promise: if the child can only reach the account through the guardian, then the guardian can finish the upgrade alone, and a guardian who can finish the upgrade alone can walk away with the child's identity.

### B — A profile on a household device

The household signs in once on a device it owns. Every member of the home, child or not, appears on it as a profile. The child touches their name and gives a PIN.

- **Good:** No secret to deliver and nothing for the child to type but four digits. It matches the shared family tablet, which is the device we expect to be real in most homes.
- **Cost:** It anchors the account to a household, which is the exact mistake option B of [[0006-a-minor-is-an-account-kind-not-a-household-role]] made one level up. A child in two homes needs the device trusted in both, and the second household must be able to set it up without being able to see the first. A child with their own phone cannot use it. And a device the household trusts is a device any member of the household can take the child's seat on.

### C — A handle the guardian chooses, a PIN the child sets, and a one-time code between them

The guardian gives the account a **handle** when they make it — a short name, unique in the product, that is not an email address. The system returns a **claim code**, used once and short-lived, and the guardian gives it to the child. The child enters the handle and the claim code, sets a **PIN**, and from then on signs in with the handle and the PIN, on any device. The guardian issues a new claim code whenever the child needs one, which is also the only reset.

- **Good:** The credential belongs to the account rather than to a home or a device, which is what [[0006-a-minor-is-an-account-kind-not-a-household-role]] requires: the child signs in at either parent's house, on a shared tablet or on their own phone, with the same two things. The guardian never learns the PIN, so the child has something of their own and the upgrade in [[0007-no-age-and-one-way-to-a-full-account]] can genuinely require the child. The reset path and the recovery path are the same act, so there is nothing extra to specify when a child forgets.
- **Cost:** Three new words, and a handle that has to be unique across the whole product — so a household that wants `lucas` may get something with a number on the end. A PIN is a weak secret, and it is the only secret, so it has to be paired with an identifier a stranger does not hold and with a stop after repeated wrong tries. The claim code has to be handed over in the real world, and a guardian who loses it before the child uses it has to ask for another.

## Decision

Option C.

**Making the account.** Any full account makes a minor account and becomes its guardian by that act. It gives a **name** and a **handle**; a picture is optional. It gives nothing else — no email address, and no date of birth, because the product holds no age for anybody. No household is involved and none has to exist.

**The handle** is how the account is identified at sign-in. It is unique across the product, it is chosen by the guardian, and only the guardian changes it. It is not an address: nothing is ever sent to a handle, and nobody uses a handle to find a child.

**The claim code** is the first way in, and the only one. The system issues it to the guardian when the account is made. It is used once, it expires, and it carries no authority of its own — it does nothing but let a child set a PIN on the account named by the handle.

**The PIN** is the child's, and the child sets it when they claim the account. Nobody sees it, including the guardian. The child changes it whenever they like.

**Reaching the account again.** The guardian issues a new claim code at any time. The new code clears the PIN, and the child sets another. That single act covers a child who forgot, a child whose PIN somebody else learned, and a child who never claimed the account in the first place. A guardian cannot set a PIN, only clear it.

**After too many wrong tries** the account stops accepting the PIN until the guardian issues a new claim code, and the guardian is told it happened.

**What the guardian sees:** whether the child has claimed the account, when the child last signed in, whether a claim code is waiting, and that the account stopped accepting wrong tries. Not the PIN.

**What the child may change:** their picture and their PIN. Not their name and not their handle, because the household knows whose work a task is by the name, and the handle identifies the account.

**Finishing the upgrade.** The child's half of [[0007-no-age-and-one-way-to-a-full-account]] is done from inside the account, signed in. The child gives an email address not already on another account, and a password. The handle and the PIN stop working at that moment, and the account is reached the way any full account is reached.

**Addressing an invitation to a minor account** does not use the handle. A household addresses it to the **guardian**, and the guardian chooses which of the minor accounts they hold it applies to when they accept. Nothing is confirmed to the household until the guardian answers.

**Making a minor account does not put it in a household.** An invitation is still the one door in, including the one a guardian who runs the household sends to their own child and answers themselves.

## Reason

Option A lost on what it would have meant for the child, not on effort. A minor in this product is a full member of the work — that is the whole of [[0006-a-minor-is-an-account-kind-not-a-household-role]] — and a person who cannot open the app is not running their own part of anything. The decisive argument, though, is the upgrade. [[0007-no-age-and-one-way-to-a-full-account]] protects a child's identity with one sentence: it does not happen without the child. That sentence needs the child to be able to act, and option A removes the only place a child can act from.

Option B is the better-looking wrong answer, and it is wrong for a reason we have already paid for once. We moved the facts about a child off a household role and onto the account, and then [[0006-a-minor-is-an-account-kind-not-a-household-role]] had to move the account out of the household's possession as well, because a household is the wrong size of thing to hold a person's identity. A credential that only works on a device a household set up puts it straight back: the child of separated parents again needs two homes to each do something, and the two homes again have to know about each other. The shared tablet is real, and option C runs on it — a tablet where two children each know their own handle and PIN is the same tablet, without the household owning the way in.

The handle is the part most likely to be argued with, so here is what it is and is not. It is a sign-in name, in the slot an email address occupies for everybody else, and it exists because a child must be identifiable to the product without being contactable by it. Making it unique across the product is the cost of that, and it is a real one — a family will be offered `lucas` and get `lucas-m`. We took it because the alternative is to scope the handle to something, and the only things available to scope it to are the household and the guardian. The household is ruled out above. The guardian would mean a child signs in by naming their parent, which is more to type, more to explain, and breaks the moment guardianship is handed on — [[modules/accounts/use-cases/03-transfer-guardianship]] would silently change how a child signs in.

A handle is deliberately **not** an address, and that is why a household invites a child through the guardian instead. If a handle could be invited, then a handle could be guessed, and guessing one would tell a stranger that a child exists and — because [[modules/household/use-cases/03-invite-a-person]] shows the inviter who the guardian is — who answers for them. There is no version of that we want. Routing the invitation through the guardian costs the household a step it was going to take anyway, because you cannot put a child in your home without the agreement of the person responsible for them, and it leaks nothing: a household that guesses wrong learns only that nobody answered.

A four-digit PIN is a weak secret and we are choosing it anyway, for a person who may be six years old and cannot be given anything stronger. What makes it defensible is that it is never the only thing between a stranger and the account: the handle is not published, the PIN is useless without it, and repeated wrong tries end the attempt rather than slowing it down. The person it does not defend against is the household itself — a sibling who watches the PIN being typed can sign in as their brother. We are accepting that. The product is for one home that mostly trusts itself, the damage available inside it is a chore closed early, and a product that defends a nine-year-old from their sister would be unusable by either of them.

The hole we are not pretending away is the guardian. A guardian can clear the PIN, so a guardian can reach the account, so a determined guardian can complete the child's half of the upgrade and hold a full account that is not theirs. We did not try to close it, because the guardian is already the account's single point of authority under [[0006-a-minor-is-an-account-kind-not-a-household-role]] and can simply delete it — which [[0007-no-age-and-one-way-to-a-full-account]] already named as the honest hostile act. What the reset does buy is the ordinary case: a guardian who starts an upgrade and forgets about it cannot finish it by accident, and a child who is actually using the app will notice their PIN stopped working. The protection is against carelessness, not against malice, and the record should say which.

Clearing the PIN rather than setting one is a small choice doing real work. If a guardian could type a PIN for the child, then a guardian could know the child's PIN, and every argument above about the upgrade needing the child would be worth nothing.

## Affects

- [[domain]] — **Account** no longer defers how a minor account begins; **Handle**, **Claim code** and **PIN** are named in the accounts module rather than here, because no other module uses them
- [[users]] — the minor persona has a way in, and may change their picture and their PIN; the guardian persona issues and reissues it
- [[modules/accounts/overview]] — the minor half of creating, signing in and self-editing is answered. The full-account half stays open
- [[modules/accounts/domain]] — **Handle**, **Claim code**, **PIN**
- [[modules/accounts/rules#a-guardian-issues-the-way-in-and-can-issue-it-again]] — the rule that carries this record
- [[modules/accounts/rules#an-account-holds-a-name-a-handle-and-a-picture]] — what is given, and who changes it
- [[modules/accounts/rules#a-minor-account-becomes-a-full-account-once]] — the open part closes: what the child supplies, and from where
- [[modules/accounts/use-cases/01-create-a-minor-account]] — the first door
- [[modules/accounts/use-cases/02-sign-in-to-a-minor-account]] — the second door, and the reissue
- [[modules/accounts/use-cases/05-finish-becoming-a-full-account]] — the child's half of the upgrade
- [[modules/household/rules#membership-starts-with-an-accepted-invitation]] — making a minor account does not put it in a household
- [[modules/household/use-cases/03-invite-a-person]] — a household addresses a minor through the guardian, never by handle

## When to revisit

**When a child needs a way in that is not a PIN.** A picture password for a child too young to hold four digits, or a phone's own lock for a teenager, are both additions rather than replacements: the handle stays, and what the handle is paired with changes. That is a new record, and a small one.

**When the product has to defend a child from their own household.** Today a PIN typed in front of a sibling is a PIN the sibling has, and we chose that. The signal to revisit is the product holding something a child would mind losing — money, or a conversation.

**When a handle being unique across the product starts hurting.** The signal is families routinely being refused the name they asked for. The fix is to scope the handle, and the only workable scope is the guardian, which costs a child's sign-in its stability when guardianship moves.

**When somebody other than the guardian has to issue a way in.** A child whose guardian has gone quiet cannot reach their account at all, which is the single-guardian cost named in [[0006-a-minor-is-an-account-kind-not-a-household-role]] showing up in a new place. The fix is there, not here.
