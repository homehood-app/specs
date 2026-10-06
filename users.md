# Users

The people who use Homehood, and the authority each one has.

**Scope of this file.** It says who the users are and what authority each one holds across the whole product. It does not say what a user may do in one area of the product. "Who can create a task", "who can close a task", "who sees another member's work" belong in that module's `rules.md` and in the **By role** section of its use cases — not here. See the **By role** section in [[templates/module/use-cases/use-case]].

The names come from [[domain]]. Organizer and member are levels of authority; minor is a property of a member. See [[decisions/0001-household-and-two-member-roles]].

## Organizer

The member who administers the household. In a family, usually a parent. In a flat share, one person or everyone.

**Access:** Creates the household, or is promoted by another organizer.

**Can:**

- Decide who belongs to the household
- See everything in the household
- Remove what another member created

**Cannot:**

- Act in a household they do not belong to
- Do another member's work for them

**Distinguishing characteristics:** The only role that can change who is in the household, the only one that sees all of it, and the only one that can remove what somebody else created.

## Member

An adult who belongs to the household but does not administer it. In a flat share, a housemate who is not the organizer.

**Access:** Joins by accepting an invitation.

**Can:**

- Manage their own work
- Give work to another member

**Cannot:**

- Change who belongs to the household
- See what does not concern them
- Remove what another member created

**Distinguishing characteristics:** Can ask anything of anybody, but sees only what concerns them and cannot change the household itself.

## Minor member

A member under the care of an organizer — in a family, a child. A flat share has none.

**Access:** Joins by accepting an invitation, or is added by an organizer.

**Can:**

- Everything a member can

**Cannot:**

- Everything a member cannot

**Distinguishing characteristics:** The only user whose view or actions may be narrowed on account of care rather than authority. **No specified behavior narrows them today** — a minor member currently has exactly a member's authority. The role exists in the vocabulary so that care-based limits have a place to attach when we decide on them.

**Not yet decided:** whether a minor's authority differs by age, and if so which age bands. Until that is decided, a use case that narrows what a minor can do must say which ages it applies to.
