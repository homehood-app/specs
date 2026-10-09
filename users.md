# Users

The people who use Homehood, and the authority each one holds.

**Scope of this file.** It says who the users are and what authority each one holds across the whole product. It does not say what a user may do in one area of the product. "Who can create a task", "who can close a task", "who sees another member's work" belong in that module's `rules.md` and in the **By role** section of its use cases — not here. See the **By role** section in [[templates/module/use-cases/use-case]].

The names come from [[domain]]. Owner, organizer and member are the three roles, in that order of authority.

**Minor is not a role, and neither is guardian.** A minor is a kind of account, held by a child, and it always carries the member role in every household it belongs to. A guardian is the one full account responsible for a minor account, outside every household. Both have a persona here because both are people the product has to serve, not because either is a rung on the ladder. See [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].

## Owner

The member who holds the household. Exactly one per household. In a family, usually a parent. In a flat share, whoever set it up.

**Access:** Creates the household, or receives ownership from the previous owner.

**Can:**

- Everything an organizer can
- Change the household itself: its data, its ownership, its existence
- Act on any member, including an organizer

**Cannot:**

- Act in a household they do not belong to
- Stop being the owner without handing ownership to another member
- Do another member's work for them

**Distinguishing characteristics:** The only member who can change the household itself, and the only member no one else can act upon.

## Organizer

A member who runs the household's day-to-day. Any number per household, including none.

**Access:** Promoted by the owner.

**Can:**

- Everything a member can
- Decide who belongs to the household, apart from the owner
- See everything in the household
- Act on the work of any member who is not the owner

**Cannot:**

- Change the household itself
- Act on the owner
- Remove another organizer

**Distinguishing characteristics:** Full authority over the household's people and work, and none over the household itself or over a peer.

## Member

A person who belongs to the household and runs their own part of it.

**Access:** Joins by accepting an invitation.

**Can:**

- Manage their own work
- Ask another member for work

**Cannot:**

- Change who belongs to the household
- See what does not concern them
- Act on another member's work

**Distinguishing characteristics:** Can ask anything of anybody, but sees only what concerns them and acts only on their own work.

## Minor

A child, holding an account a guardian made for them. In a family, a son or a daughter. A flat share has none.

In every household they belong to, a minor is a member. The difference is not what they may do inside a household — it is the account, and who answers for it.

**Access:** A guardian creates the account and hands the child a one-time code to reach it with. The child then signs in on any device with the account's own kind of name and a short secret only they know — never an email address and never a password. The child becomes a member of a household when their guardian accepts an invitation for them. See [[modules/accounts/use-cases/02-sign-in-to-a-minor-account]].

**Can:**

- Everything a member can, with nothing taken away: manage their own work, and ask any member for work
- Belong to any number of households, and hold the member role in each one
- Reach their own account, on any device, in every household they belong to
- Change their own picture, and their own secret. Their guardian cannot see the secret
- Finish making the account a full account, once their guardian has asked for it. Nobody else can finish it

**Cannot:**

- Everything a member cannot
- Change their own name, which their guardian gave them, or the name their account is identified by
- Choose which households they belong to. Their guardian answers the invitation
- Take themselves out of a household. Organizer authority there does it, and so can their guardian
- Hold the owner role, so they cannot create a household and cannot receive one
- Hold the organizer role, so they are never promoted
- Decide that their own account becomes a full one. Their guardian decides that

**Distinguishing characteristics:** A member in every way that concerns the work, and the only member who did not choose to be here and cannot choose to leave.

A minor is an account kind rather than a role — see [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]]. Nothing about a minor depends on an age, because the product holds none, and the account becomes a full one when the guardian decides — see [[decisions/0007-no-age-and-one-way-to-a-full-account]].

## Guardian

The person responsible for a child's account. In a family, a parent. Always a full account, and a person who may or may not share a household with the child.

A guardian is not a member of anything by being a guardian. Their authority is over one account, not over a home.

**Access:** They hold a full account and they made a minor account, or another guardian handed one to them. Any full account can make one, whether or not it belongs to a household.

**Can:**

- Make a minor account, and become its guardian by that act
- Hand the child the way in to their own account, and hand it over again whenever the child cannot get in
- See whether the child has reached the account, and when they were last there
- Change the child's name, the name the account is identified by, and the picture
- Accept or decline an invitation to a household on behalf of the minor they hold
- Take that minor out of any household they belong to
- Hand the minor account to another full account
- Make the minor account a full account, which ends their own guardianship of it
- Delete the minor account
- See which households the minor belongs to

**Cannot:**

- See anything inside a household they are not a member of — not the minor's tasks there, not its members, not its roles
- Act on the minor's work, in any household. A guardian who is a member of the household has their own role, and being the guardian adds nothing to it
- See the child's secret, or set one. They can clear it, which is how a child who is locked out gets back in
- Finish making the minor account a full account. They ask for it; only the child completes it
- Be rid of the account by walking away. They hand it on or they delete it
- Hold guardianship of a minor account together with anybody else. There is exactly one guardian

**Distinguishing characteristics:** The only person in the product whose authority is over an account rather than over a household, and the only one who decides something for somebody else.

See [[modules/accounts/overview]] for what a guardian does, and [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]] for why the guardian exists at all.
