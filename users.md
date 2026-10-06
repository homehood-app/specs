# Users

The people who use Homehood, and the authority each one holds.

**Scope of this file.** It says who the users are and what authority each one holds across the whole product. It does not say what a user may do in one area of the product. "Who can create a task", "who can close a task", "who sees another member's work" belong in that module's `rules.md` and in the **By role** section of its use cases — not here. See the **By role** section in [[templates/module/use-cases/use-case]].

The names come from [[domain]]. Owner, organizer and member are the three roles, in that order of authority. Minor is a property of a member, not a role. See [[decisions/0004-four-roles-owner-organizer-member-minor]].

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

## Minor member

A member under the care of the household — in a family, a child. A flat share has none. Minor is a property, so an owner or an organizer could also be a minor, although that is unusual.

**Access:** Joins by accepting an invitation, or is added by an owner or an organizer.

**Can:**

- Everything their role allows

**Cannot:**

- Nothing beyond what their role already forbids

**Distinguishing characteristics:** Sees a reduced view of the product — less on screen, for the same actions.

**Not yet decided:** exactly what is reduced, and whether it changes with age. Until that is decided, a use case that narrows what a minor sees must say what it hides.
