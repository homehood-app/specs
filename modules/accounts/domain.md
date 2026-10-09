# Accounts — Domain

Concepts specific to this module. **Account**, its two kinds, **Minor** and **Guardian** are defined in the shared [[domain]], because the household module needs them too.

## Guardianship

The relationship between one guardian and one minor account. It is what this module governs.

Guardianship exists for the whole life of a minor account and never lapses. It begins when the account is made, and it ends in exactly three ways:

| How it ends | What is left |
| --- | --- |
| Handed to another full account | The same minor account, a different guardian |
| The minor account becomes a full account | No minor account, and nobody responsible for the person but themselves |
| The minor account is deleted | Nothing |

There is no fourth way. A guardian cannot resign, because that would leave a child's account with nobody answering for it — the same gap as a household with no owner.

Guardianship is not a role and not a membership. It says nothing about where either account belongs.

## Handle

The name a minor account is identified by when a child signs in. It sits where an email address sits for a full account, and it is not one.

A handle is unique across the whole product, so a household that asks for a name somebody already has is offered another. The guardian chooses it when they make the account, and only the guardian changes it.

A handle is **not an address**. Nothing is ever sent to one, and nobody finds a child by one — a household invites a minor through its guardian instead. See [[decisions/0014-a-child-signs-in-with-a-handle-and-a-pin]].

A handle belongs to a minor account only. It is released when the account becomes a full account, because a full account is reached by its email address.

## PIN

The short secret a child signs in with, next to their handle. It stands where a password stands for a full account.

The child sets it, the child changes it, and nobody else ever sees it — not a guardian, not an owner. A guardian can clear a PIN, by issuing a new claim code, and can never set one. That is what makes it the child's.

## Claim code

A short code, used once and short-lived, that lets a child reach a minor account for the first time and set a PIN on it.

The system issues it to the guardian, who gives it to the child. It carries no authority of its own: it opens nothing but the setting of a PIN on the account its handle names.

A new claim code is also the only reset and the only recovery. Issuing one clears the PIN and changes nothing else about the account.
