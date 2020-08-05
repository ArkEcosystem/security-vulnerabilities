# Pool poisoning could stop delegates forging any transactions
**Identifier:** Core-SV-053
## Cause:
There was a low limit on the number of transactions returned from the transaction pool for inclusion in a new block prior to filtering them. A bad actor could repeatedly spam the pool with hundreds or thousands of invalid transactions with a very high fee - which, as they were invalid, would never be forged, so the actual cost was zero - but the high fee meant they would take precedence over all genuine transactions in the pool, so after filtering, the block would be empty.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3905
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.49