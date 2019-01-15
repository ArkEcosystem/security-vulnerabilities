# Generating new Ark using multi signature transaction
**Identifier:** Core-SV-0002

## Cause
In a multi-signature transaction, the transaction handler only verified the signatures and did not properly conduct balance checks. This made it possible to generate new ARK tokens on the network utilizing a multi-signature transaction.

>Reported by: delegate fun

## Solution
Perform wallet balance checks for multi signature transactions.

**Patch:** https://github.com/ArkEcosystem/core/pull/1658

## Status
Closed.
**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.0.16


