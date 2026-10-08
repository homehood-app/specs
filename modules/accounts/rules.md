# Accounts — Business Rules

## Every minor account has exactly one guardian

A minor account is never unheld, and never held by two.

- Every minor account has exactly one guardian, from the moment it exists
- A guardian is a full account. A minor account cannot be a guardian
- One guardian can hold several minor accounts. A household with three children has three accounts and one person answering for them
- Guardianship moves only by being handed to another full account, and the new guardian must accept it — see [[use-cases/01-transfer-guardianship]]
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
- The change is one way. A full account never becomes a minor account
- It is the same account afterwards, not a new one. Every membership, every task where the person is requester or executor, and every comment they wrote is untouched and still theirs
- The account keeps the member role in each household it belongs to. Becoming a full account is not a promotion, and the owner promotes it afterwards or not — see [[household/use-cases/06-change-a-members-role]]
- Afterwards the account has no guardian, and cannot be given one
- What the child supplies, and how, is part of how a child reaches a minor account. Not specified yet — see [[overview]]

## Only the guardian ends a minor account

A minor account outlives any household it was ever in.

- Only the guardian deletes a minor account — see [[use-cases/03-delete-a-minor-account]]
- Being removed from a household does not end the account. The minor keeps every other membership, and keeps the account with none
- Deleting a household does not end the minor accounts that were in it — see [[household/use-cases/10-delete-a-household]]
- Deleting a minor account ends every membership it holds. Each household keeps the record of what the child did there, exactly as for any former member — see [[household/rules#a-former-member-stays-on-what-they-left-behind]]
- A deleted account is not recoverable. Whether a household can be given a way back is part of how a minor account is created, and is not specified yet
