# Delayed block propagation causes the next delegate to miss its block
**Identifier:** Core-SV-015

## Cause: 
If a delegate forges a block but is late broadcasting it, the next delegate in line will forge at the wrong height as it will not have received the previous block. By the time it attempts to broadcast the block, the previous delegate's delayed block will have been received by most (or all) of the network, meaning the newly forged block at the same height will be rejected and thus the delegate will miss its block.

This could be done maliciously to deliberately prevent the next delegate in line from forging, or by accident if there is sufficient network latency. 

>Reported by: delegate fun

## Solution
Mitigation was acheived by using the height from the network rather than the local node when forging a block.

**Patch:** 
https://github.com/ArkEcosystem/core/pull/2231

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.3
