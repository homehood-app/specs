---
decision: 0006
date: 2026-10-08
status: accepted
supersedes: 0004-four-roles-owner-organizer-member-minor
superseded-by:
---

# 0006 — A minor is an account kind, not a household role, and a guardian holds it

## Question

[[0004-four-roles-owner-organizer-member-minor]] made minor the fourth rung of the household's ladder: owner, organizer, member, minor. Writing down what the fourth rung actually narrows showed that almost nothing about a minor is about the household. What is different about a child is the **account**: a child does not sign up, does not hold an email address, and does not choose where they live. Somebody makes the account for them.

So minor is a kind of account. That leaves a second question, and it is the one that matters: **who is responsible for a minor account?**

## Options

### A — A fourth household role

Minor is the lowest rung: owner, organizer, member, minor. Every person signs up the same way, and the household decides what a person is once they are inside it.

- **Good:** One ladder, one list, nothing new to name. The **By role** table answers the minor case in every use case, because minor has a row.
- **Cost:** It puts the difference in the wrong place and so cannot express the difference at all. A role says what a person may do *inside a household*. It cannot say "this person needs no email address", "this person signs in another way", or "somebody else answers for this person" — those are facts about an account, and a role has no way to hold them. Worse, as a role it implies a child signs themselves up like everybody else and is then labelled, which is not how a child gets into a family app.

### B — An account kind, and the household that made it is responsible

Three household roles. A minor is a kind of account, created by a household for a child who lives in it, belonging to that household and to no other, ending when the membership ends.

- **Good:** Each fact about a child lands on the account instead of on a role. The household's ladder goes back to three real tiers of authority. Nothing new to name beyond the account kind.
- **Cost:** It breaks on two ordinary families. **A child of separated parents lives in two homes** and this allows exactly one, so one parent's household is the real one and the other cannot have the child at all. **A child grows up**, and an account that cannot outlive its household cannot become that person's own account either: the teenager signs up fresh and the household ends with a former member and a current member who are the same human, linked by nothing. Both failures have the same cause — a household is the wrong size of thing to be responsible for a person's identity.

### C — An account kind, and a guardian is responsible

Three household roles. A minor is a kind of account, and every minor account has exactly one **guardian**: a full account, outside every household, that answers for it. The guardian decides where the child belongs, when the child leaves, when the account becomes a full account, and when it ends.

- **Good:** Both failures of option B stop being household questions, because the household is no longer asked. A child belongs to two homes because their guardian accepted two invitations. A child grows up because their guardian released the account, and the account is the same one, so the memberships and the history come with it. It also names the person who was already implied and unwritten: somebody made this account, and that somebody is accountable for it.
- **Cost:** A third concept, and the one the reader has to hold hardest, because guardianship is neither a role nor a membership and looks like both. It creates authority that crosses a household boundary — a guardian can take a child out of a home they cannot see into — which has to be stated carefully every time or it reads like a leak. And one guardian is a single point of failure: if that person stops caring, nobody else can act for the child, and the only remedy is a transfer that only they can start.

## Decision

Option C.

**The household has three roles:** owner, organizer, member. In that order of authority. Everything [[0004-four-roles-owner-organizer-member-minor]] settled about the owner stands, and so does the neutral vocabulary from [[0001-household-and-two-member-roles]]: we say household, not family.

**A minor is a kind of account.** A minor always holds the member role in every household they belong to, and a minor's authority over the work is a plain member's, in full.

**Every minor account has exactly one guardian** — a full account, responsible for it, outside every household.

What is true of a minor and of nobody else:

- A minor does not decide where they belong. Their guardian accepts or declines an invitation for them
- A minor cannot leave a household. Organizer authority in that household takes them out, and so can their guardian
- A minor cannot hold the owner role, so cannot create a household and cannot receive one
- A minor cannot hold the organizer role, so is never promoted
- A minor does not decide what their own account is. Their guardian makes it a full account — see [[0007-no-age-and-one-way-to-a-full-account]]

What is true of a guardian:

- Exactly one per minor account, always, and never two. The holder cannot resign — they hand the account on, release it, or delete it
- Guardianship gives no authority inside any household and no authority over any task
- A guardian sees which households the minor belongs to, and nothing inside the ones they are not a member of
- A guardian who **is** a member of a household sees what their own role shows them and no more

Everything else about a minor is a plain member's, including what they see inside a household. A minor sees who the owner is, sees which members are organizers, and sees their own work exactly as any member does.

Out of scope here, deliberately: how a minor account is created, and how a child signs in to it. A minor account needs no email address and no password of the usual kind, and the mechanism is a separate question.

## Reason

The test that moved minor off the role was a single question: can a role say "this person needs no email address"? It cannot. A role is a statement about authority inside one household, and the things that make a child different are statements about the account. Putting them on a role meant they could not be written down at all, which is exactly what happened: the fourth rung sat in the spec for two pull requests with nothing in it.

Moving minor onto the account also fixed the ladder. Owner, organizer and member are three tiers of authority, each one able to do something the next cannot. "Minor" was never that: it was a member with a different front door. A ladder that mixes authority with provenance is a ladder that cannot be reasoned about.

The guardian is the second half, and we got it wrong first. Option B left the account owned by the household that made it, which felt natural and was the same mistake one level down: we had moved the facts off the role and onto the account, and then made the account a possession of a household. An account a household owns can only ever live there, and only that household can let it go. Both of the cases that broke it — two homes, and growing up — are the same question in different clothes: *which household decides?* Every answer to that question is bad, because no household has standing to decide who a child is. A guardian removes the question. Nobody is asked, because the person responsible for the account is the one who answers.

Choosing one guardian over several was a close call and it is the sharpest cost we took. Several equal guardians — the shape an organizer has, where no peer can remove another — would let both separated parents act for the child, and neither could lock the other out. One guardian means every decision about the child's account goes through one person, who may be an ex-partner who does not answer. We took one anyway: two guardians over one child invite a fight the product cannot referee, and a tie between two people with equal authority over a child's account has no good resolution in software. One guardian with a clean transfer is a worse day and a simpler truth. The transfer is what makes it survivable, so the transfer is not optional — see [[modules/accounts/use-cases/01-transfer-guardianship]].

The word is **guardian** and not "parent" or "responsible adult". "Parent" is the family vocabulary we rejected in [[0001-household-and-two-member-roles]]. "Adult" claims an age, and the product holds no age for anybody — we would be asserting something we never checked. Guardian names a relationship between two accounts, which is exactly what the product holds.

One cost of option C is worth naming plainly because it will look like a bug: **a guardian can act on a membership inside a household they cannot see.** They can take their child out of the other parent's home without seeing one task in it. That is deliberate. The authority is over the account, and ending a membership is an act on the account, not a reading of the household. The consequence is that a guardian who removes a child settles none of the child's work, and the household is left to resolve it — see [[modules/household/use-cases/08-remove-a-member]].

The restrictions we considered and left out are as important as the ones we kept. A minor does not see less of the household: not the roles of other members, not who the owner is, not whether a task of theirs is waiting on somebody else. Those were in an earlier draft and they are gone, because a restriction is worth writing only when it changes what somebody can do. Hiding a label on a screen does not.

## Affects

- [[domain]] — **Account** has two kinds and one change of kind; **Guardian** is a new concept; **Minor** is an account kind; **Invitation** is answered by a guardian when it is addressed to a minor
- [[users]] — three roles, the minor persona, and the guardian persona. Neither of the last two is a rung
- [[modules/accounts/overview]] — a new module for the account and its life
- [[modules/accounts/rules#every-minor-account-has-exactly-one-guardian]] — one guardian, always, and no resigning
- [[modules/accounts/rules#a-guardian-decides-the-account-not-the-household]] — what guardianship reaches, and what it does not
- [[modules/accounts/use-cases/01-transfer-guardianship]] — the only way guardianship moves
- [[modules/household/rules#a-minor-is-a-member-and-stays-a-member]] — no promotion, no ownership
- [[modules/household/rules#a-minors-memberships-are-their-guardians-to-decide]] — any number of households, and who can end one
- [[modules/household/rules#membership-starts-with-an-accepted-invitation]] — one door in, for every kind of account
- [[modules/household/rules#a-household-is-a-closed-boundary]] — a guardian stays outside it
- [[modules/household/use-cases/01-create-a-household]] — a minor cannot start one
- [[modules/household/use-cases/03-invite-a-person]] — a minor can be invited, and the invitation goes to the guardian
- [[modules/household/use-cases/05-answer-an-invitation]] — the guardian answers for the minor
- [[modules/household/use-cases/06-change-a-members-role]] — a minor's role cannot change, and the household cannot make one eligible
- [[modules/household/use-cases/07-transfer-ownership]] — a minor cannot receive the household
- [[modules/household/use-cases/08-remove-a-member]] — two actors can take a minor out, and the account survives it
- [[modules/household/use-cases/09-leave-a-household]] — a minor is refused
- [[modules/household/use-cases/10-delete-a-household]] — minor accounts outlive the household
- [[modules/tasks/rules#a-minor-works-like-any-other-member]] — nothing in the work is reduced, and a guardian has no part in it
- [[templates/module/use-cases/use-case]] — the **By role** table keeps four rows, and gains a fifth where a guardian acts

## When to revisit

**When one guardian is not enough.** This is the cost we chose and the most likely reason this record changes. The signal is a separated parent who cannot get their child into their own home because the other parent will not answer. The fix would be several equal guardians, no one of whom can remove another — the organizer shape. Everything else in this record survives that change.

**When the product holds money.** A household budget is the first thing we expect a minor not to see, and it is the restriction Tiago named first. It does not need a new record — it needs a rule in the module that owns money, and a minor row that says `Nothing.`

**When a guardian turns out to be the wrong person.** Today nobody can take a minor account from its guardian, by design: the alternative is a product that adjudicates families. If a household ever has to be protected from a child's guardian, that is a new record and a hard one.
