# Pool wallet manager could lock up funds by not updating multipayment balances

**Identifier:** Core-SV-039

## Cause:

The transaction pool wallet manager balance did not always increase when receiving a multipayment transaction. This was because transactionHandler.applyToRecipient in acceptChainedBlock was only called if there was a matching recipientId already in the pool wallet manager. In the case of multipayments, the recipientId always matches the senderId, as the actual recipients are stored in a separate asset field instead, so this could have been manipulated to lock the amount of the multipayment to prevent the recipient from accessing the funds as their pool wallet manager balance did not increase if the recipient's address was present in the pool wallet manager but the sender's address was not. This prevented the recipient from sending a transaction for an amount that is greater than the sum of non-multipayment transactions in their account.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3570

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.21
