# Nonce comparison took too long to complete when fetching unconfirmed transactions to forge
**Identifier:** Core-SV-042
## Cause:
By continually filling the transaction pool with valid transactions, it will grow at a rate faster than the transactions in the pool can be consumed by forging blocks on the network. When it reached a certain threshold (amount varies depending on node specification, but always before reaching the upper limit even on the most powerful nodes), the call to getUnconfirmedTransactions would time out due to the nonce comparison in sortAll() of memory.ts in the core-transaction-pool package.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3667
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.34
