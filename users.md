# Users

The people who use Homehood, and the authority each one holds.

**Scope of this file.** It says who the users are and what authority each one holds across the whole product. It does not say what a user may do in one area of the product. "Who can create a task", "who can close a task", "who sees another member's work" belong in that module's `rules.md` and in the **By role** section of its use cases — not here. See the **By role** section in [[templates/module/use-cases/use-case]].

The names come from [[domain]]. Owner, organizer and member are the three roles, in that order of authority.

**Minor is not a role.** It is a kind of account, held by a child the household made it for, and it always carries the member role. It has a persona here because it is a person the product has to serve, not because it is a rung on the ladder. See [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]].

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

A child of the household, holding an account the household made for them. In a family, a son or a daughter. A flat share has none.

A minor is a member. The difference is not what they may do inside the household — it is the account.

**Access:** A member with organizer authority creates the account inside the household, and the child is a member from that moment. There is no invitation and nothing to accept. The account needs no email address of its own. How it is created, and how a child signs in, is not specified yet.

**Can:**

- Everything a member can, with nothing taken away: manage their own work, and ask any member for work

**Cannot:**

- Everything a member cannot
- Belong to a second household
- Take themselves out of the one they are in. A member with organizer authority does it
- Hold the owner role, so they cannot create a household and cannot receive one
- Hold the organizer role, so they are never promoted
- Become a full account, at any age

**Distinguishing characteristics:** A member in every way that concerns the work, and the only member who did not choose to be here and cannot choose to leave.

A minor is an account kind rather than a role — see [[decisions/0006-a-minor-is-an-account-kind-not-a-household-role]]. Nothing about a minor changes with age, and a child who is ready for their own account signs up for a full one and is invited as a member — see [[decisions/0007-no-age-and-no-conversion-of-a-minor-account]].
