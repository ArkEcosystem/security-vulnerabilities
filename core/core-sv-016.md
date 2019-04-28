# Receiving a block containing non-valid transactions causes peers to rollback 
**Identifier:** Core-SV-016

## Cause: 
A received block containing a transaction that cannot be applied causes all peers to roll back.

When a block is received, the accept block handler (core/packages/core-blockchain/src/processor/handlers/accept-block-handler.ts) triggers a rollback if an error is raised in the try...catch code block. This always happens if there is a transaction that cannot be applied. In this case it seems unnecessary to roll back multiple blocks when it is a case that the current block cannot be applied due to the transactions within it (rather than, say, a mismatched last block ID which would suggest a fork).


Even though this can be triggered by a malicious delegate, I think that the consequences are more severe than a mere inconvenience, since it can be potentially exploited to deliberately deprive other delegates of their forging rewards as it will make them miss blocks, and multiple delegates missing blocks and rolling back also results in a significantly degraded and slowed network. It can even bring down all delegates, stop the chain, and lose transactions. Nonetheless, there are other ways to trigger this as well that do not necessarily require a malicious delegate, as outlined above.
>Reported by: delegate fun

## Solution

**Patch:** 
https://github.com/ArkEcosystem/core/pull/2231

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.3
