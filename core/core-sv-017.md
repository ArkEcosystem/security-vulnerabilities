# Second Signature Transaction Broadcast/Sign/Order 
**Identifier:** Core-SV-017

## Cause
Transactions signed with a second signature prior to the second signature registration being forged will halt the blockchain. A node that receives a second signature registration, immediately followed by a transaction signed with that second signature prior to the second signature registration being forged in a block, will be unable to forge a new block as the second transaction will be accepted by the node and added to its transaction pool but will not validate in a block since the second signature registration was not forged yet. As transactions are broadcasted to all nodes, this will stop the chain until the pools are cleared as nobody will be able to forge a block.

This does not require a delegate to execute.

>Reported by: [alessio](https://github.com/alessiodf)

A patch has been supplied by delegate fun to ensure that the transaction pool will not accept a transaction from a sender if their second signature registration remains unforged in the pool.

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/2458

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.3
