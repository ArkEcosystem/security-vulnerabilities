# A forged second signature registration does not invalidate existing transactions from the same sender in the transaction pool 
**Identifier:** Core-SV-018

## Cause
It is possible to stall the blockchain, by manipulating second signature registrations. It involves broadcasting a transaction from a wallet without a second signature, then registering a second signature for that wallet which is forged prior to the initial transaction being forged.

This does not require a delegate to execute.

>Reported by: delegate fun

## Solution

**Patch:**

https://github.com/ArkEcosystem/core/pull/2659
https://github.com/ArkEcosystem/core/pull/2635
https://github.com/ArkEcosystem/core/pull/2622 

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.4.0