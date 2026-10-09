# Accounts — Business Rules

## An account holds a name, a handle and a picture

What the product knows about a person, and no more. See [[decisions/0014-a-child-signs-in-with-a-handle-and-a-pin]].

- A minor account holds a **name**, required, and a **handle**, required and unique across the product. A picture is optional
- It holds no email address, and no password. Those are what a full account holds
- It holds **no date of birth**, and neither does any other account. The product holds no age for anybody, and no rule depends on one — see [[decisions/0007-no-age-and-one-way-to-a-full-account]]
- The guardian gives the name and the handle when they make the account, and the guardian changes either of them afterwards
- The child changes their **picture** and their **PIN**, and nothing else. They cannot change their own name, because the household knows whose work a task is by the name, and they cannot change their handle, because it identifies the account
- A name is not an identifier. Two accounts can carry the same name; two accounts cannot carry the same handle
- What a full account holds, and who changes it, is not specified yet — see [[overview]]

## A guardian issues the way in, and can issue it again

A child reaches their account with something of their own, and the guardian is who hands it over the first time. See [[decisions/0014-a-child-signs-in-with-a-handle-and-a-pin]].

- A child signs in with the account's **handle** and their own **PIN** — see [[use-cases/02-sign-in-to-a-minor-account]]
- A new minor account cannot be signed in to. It is reached first with a **claim code**, which the system issues to the guardian and the guardian gives to the child
- A claim code is used once and expires. Using it sets a PIN, and the PIN is the way in from then on
- Only the child knows the PIN. A guardian cannot see it and cannot set one. A guardian can **clear** it, by issuing a new claim code, and that is the only reset and the only recovery
- After too many wrong tries the account stops accepting the PIN until the guardian issues a new claim code, and the guardian is told that it happened
- The guardian sees whether the account has been claimed, when it was last signed in to, and whether a code is waiting. No household role sees any of it, and no household role can issue one
- The way in belongs to the account, not to a household and not to a device. The same handle and PIN work in every household the child belongs to, and on any device
- A handle is not an address. Nothing is sent to one, and a household invites a minor through its guardian — see [[household/use-cases/03-invite-a-person]]
- How a full account signs up and signs in is not specified yet — see [[overview]]

## Every minor account has exactly one guardian

A minor account is never unheld, and never held by two.

- Every minor account has exactly one guardian, from the moment it exists
- A guardian is a full account. A minor account cannot be a guardian
- One guardian can hold several minor accounts. A household with three children has three accounts and one person answering for them
- Guardianship moves only by being handed to another full account, and the new guardian must accept it — see [[use-cases/03-transfer-guardianship]]
- A guardian cannot resign, and cannot be removed by anybody. To stop being a guardian they hand the account on, make it a full account, or delete it
- A guardian's own account cannot end while they hold a minor account. They deal with every minor account they hold first. How a full account is deleted is not specified yet
- The guardian does not have to be a member of any household the minor belongs to, and never has to be

## A guardian decides the account, not the household

Guardianship is authority over one account. It is not authority inside a home, and it does not reach the work.

- A guardian accepts or declines an invitation addressed to the minor they hold — see [[household/use-cases/05-answer-an-invitation]]
- A guardian takes the minor out of any household they belong to — see [[household/use-cases/08-remove-a-member]]
- A guardian sees which households the minor belongs to, and the name of each one
- A guardian sees nothing else inside a household they are not a member of: not the minor's tasks, not the other members, not who the owner is — see [[household/rules#a-household-is-a-closed-boundary]]
- A guardian who **is** a member of a household sees what their own role lets them see, and no more. Being the guardian adds nothing — see [[tasks/rules#a-minor-works-like-any-other-member]]
- A guardian cannot act on the minor's work anywhere: not create, not close, not archive, not delete, not comment
- A guardian cannot give the minor a role, or take one away. Role is the owner's, in the household — see [[household/use-cases/06-change-a-members-role]]

## A minor account becomes a full account once

This is how a child grows up without losing what they did.

- The guardian decides it. No household is asked, and no household can refuse — see [[decisions/0007-no-age-and-one-way-to-a-full-account]]
- It needs no age, because the product holds none. A guardian who thinks the child is ready is the whole test
- The guardian starts it, and it finishes only when the account has an email address and a password of its own. Nothing happens to the child's account without the child
- **The child finishes it from inside the account, signed in.** The child gives an email address that is on no other account, and a password. The guardian cannot give either — see [[use-cases/05-finish-becoming-a-full-account]]
- The handle and the PIN stop working at that moment, and the handle is released. A full account is reached by its email address
- The change is one way. A full account never becomes a minor account
- It is the same account afterwards, not a new one. Every membership, every task where the person is requester or executor, and every comment they wrote is untouched and still theirs
- The account keeps the member role in each household it belongs to. Becoming a full account is not a promotion, and the owner promotes it afterwards or not — see [[household/use-cases/06-change-a-members-role]]
- Afterwards the account has no guardian, and cannot be given one
- It is one of the three ways guardianship ends, and the only one the child takes part in

## Only the guardian ends a minor account

A minor account outlives any household it was ever in.

- Only the guardian deletes a minor account — see [[use-cases/06-delete-a-minor-account]]
- Being removed from a household does not end the account. The minor keeps every other membership, and keeps the account with none
- Deleting a household does not end the minor accounts that were in it — see [[household/use-cases/10-delete-a-household]]
- Deleting a minor account ends every membership it holds. Each household keeps the record of what the child did there, exactly as for any former member — see [[household/rules#a-former-member-stays-on-what-they-left-behind]]
- A deleted account is not recoverable, and no household can be given a way back to one. A household that wants the child again asks somebody to make a new minor account, and it is a new account with nothing on it — see [[use-cases/01-create-a-minor-account]]
- The handle of a deleted account is released, and another account can take it
