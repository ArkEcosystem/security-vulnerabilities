# Race condition can result in blocks containing already forged transactions
**Identifier:** Core-SV-020

## Cause
If a node receives a high volume of transactions entering the transaction pool in a short time period, it will not filter out all the recently forged transactions from incoming blocks. This means that when a delegate tries to forge, it may include already forged transactions in its block, which will then be rejected by the network, causing the affected delegates to miss blocks until their pools are clean.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:**

- https://github.com/ArkEcosystem/core/pull/2659
- https://github.com/ArkEcosystem/core/pull/2635
- https://github.com/ArkEcosystem/core/pull/2622

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.4.0