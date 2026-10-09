---
status: draft
updated: 2026-10-08
superseded-by:
---

# Answer an invitation

As the person who answers for the invited account, I want to accept or decline so that the invited person joins the household or stays out of it.

**Actors:** [[users#member]], [[users#guardian]]

## Pre-conditions

- An invitation to the account exists in state `Pending`
- The actor is the holder of that account, or its guardian if it is a minor account

## Main flow

1. The actor opens the invitation.
2. The actor accepts it.
3. The system sets the invitation to `Accepted`.
4. The system makes the invited person a member of the household, with the plain member role.

## Alternative flows

### The actor declines

1. The system sets the invitation to `Declined`.
2. The invited person does not become a member.
3. The household sees the answer, and who gave it.

### The invitation is to a minor account

1. The guardian answers it. The child is not asked and cannot answer — a child does not choose which homes they live in.
2. The invitation was addressed to the guardian, not to the child, so **the guardian chooses which of the minor accounts they hold it applies to** before they accept. The household said which child it meant in words; the guardian decides which account that is — see [[03-invite-a-person]].
3. On accept, the minor is a member with the plain member role, like any member, and works exactly as any member does. See [[tasks/rules#a-minor-works-like-any-other-member]].
4. The guardian does not become a member of the household by answering. If they were not a member before, they are not one now, and they see nothing inside it.
5. The household sees that the guardian answered, who they are, and which child joined.

### The guardian holds no minor account the invitation could be for

1. The guardian declines, and the household learns only that it was declined.
2. Nothing tells the household whether the guardian holds that child, or any child. A household cannot find a child through the product — see [[decisions/0014-a-child-signs-in-with-a-handle-and-a-pin]].

### The invited person already belongs to other households

1. The system adds this membership to the others. Nothing is replaced.
2. This holds for a minor too. A child of separated parents belongs to both homes, and each one sees only its own work.

## Exception flows

### The invitation is no longer pending

1. The system refuses and says the invitation is already answered or was revoked.
2. Nothing changes.

### The household no longer exists

1. The system refuses and says the household is gone.
2. Nothing changes.

### A minor tries to answer their own invitation

1. The system refuses and says their guardian answers it.
2. Nothing changes. There is no age at which this changes — what changes it is the account becoming a full account. See [[accounts/use-cases/04-make-a-minor-account-a-full-account]].

## Post-conditions

- The invitation is `Accepted` or `Declined`, and cannot be answered again
- On accept, the invited person is a member of the household, with the plain member role
- On accept of a minor's invitation, the minor keeps every other household they belong to, and their guardian is unchanged
- Nobody became a member by answering for somebody else

## By role

| Role | Sees | Can do |
| --- | --- | --- |
| Owner | The answer to any invitation to the household, and who gave it | Nothing. Nobody in the household answers for an invited person |
| Organizer | The answer to any invitation to the household, and who gave it | Nothing |
| Member | Their own pending invitation | Accept it or decline it |
| Minor | Nothing of this use case. They are not shown the invitation and are not asked | Nothing. Their guardian answers |
| Guardian | Every pending invitation to a minor they hold, and which household it is from | Accept it or decline it for the minor |

## Applied business rules

- [[rules#membership-starts-with-an-accepted-invitation]] — accepting is what makes a person a member, whoever does the accepting
- [[rules#a-minors-memberships-are-their-guardians-to-decide]] — the guardian answers, and the child does not
- [[rules#a-household-is-a-closed-boundary]] — answering for a minor puts the child inside the household and leaves the guardian outside it
