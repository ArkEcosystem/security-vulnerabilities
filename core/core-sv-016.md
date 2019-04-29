# Receiving a block containing non-valid transactions causes peers to rollback 
**Identifier:** Core-SV-016

## Cause: 
A received block containing a transaction that cannot be applied causes all peers to roll back.

When a block is received, the accept block handler (`core/packages/core-blockchain/src/processor/handlers/accept-block-handler.ts`) triggers a rollback if an error is raised in the `try...catch` code block. This always happens if block contains a transaction that cannot be applied. In this case it seems unnecessary to roll-back multiple blocks when it is a case that the current block cannot be applied due to the transactions within it.

>Reported by: delegate fun

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.3
