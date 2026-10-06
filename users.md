# Users

Every use case must say what each of these users sees and can do. See the **By role** section in [[templates/module/use-cases/use-case]].

The names come from [[domain]]. Organizer and member are permission levels; minor is a property of a member. See [[decisions/0001-household-and-two-member-roles]].

## Organizer

The member who administers the household. In a family, usually a parent. In a flat share, one person or everyone.

**Access:** Creates the household, or is promoted by another organizer.

**Can:**

- Create a household
- Invite people to the household, and remove members
- Create a task for themselves or for any other member
- Edit, start, comment on, close, archive and delete a task

**Cannot:**

- Act in a household they do not belong to

**Distinguishing characteristics:** The only role that can change who is in the household. The only role that can assign work to someone else.

## Member

An adult who belongs to the household but does not administer it. In a flat share, a housemate who is not the organizer.

**Access:** Joins by accepting an invitation.

**Can:**

- Create a task for themselves
- Start, comment on and close their own task
- See the household's tasks and who owns each one

**Cannot:**

- Invite or remove people
- Assign a task to another member

**Distinguishing characteristics:** Full control over their own work, no control over other people's.

## Minor member

A member under the care of an organizer — in a family, a child. A flat share has none.

**Access:** Joins by accepting an invitation, or is added by an organizer.

**Can:**

- See the tasks they own
- Start, comment on and close their own task

**Cannot:**

- Invite or remove people
- Assign a task to another member

**Distinguishing characteristics:** The only user whose view and permissions may be narrowed on account of care rather than permission level.

**Not yet decided:**

- Whether closing a task needs an organizer to confirm it
- Whether a minor sees the whole household's tasks or only their own
- Whether permissions differ by age, and if so which age bands

Until these are decided, a use case that touches a minor must state its assumption in the **By role** section rather than leave the row blank.
