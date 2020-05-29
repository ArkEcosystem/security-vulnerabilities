# Tree memory structure exceeded maximum call stack size when fetching unconfirmed transactions to forge
**Identifier:** Core-SV-043
## Cause:
By continually filling the transaction pool with valid transactions with an increasing fee of one arktoshi each time, the call to getUnconfirmedTransactions when forging would error out as the maximum call stack size would quickly be exceeded. At that point the network would stall as nobody would be able to forge any new blocks since the call to request the transactions to forge would always fail. 
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3678
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.36
