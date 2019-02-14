# Transactions near to the HTTP POST payload size limit can stop delegates forging and halt the chain
**Identifier:** Core-SV-013

## Cause: 
Transactions near to the HTTP POST payload size limit can stop delegates forging and halt the chain. 

The maximum HTTP payload is 1048576 bytes but there was no logic to ensure that blocks only contained transactions that would fit in a block below that size limit. It was possible for any network user to send deliberately oversized transactions that would approach (but not exceed) this limit. Such oversized transactions could be easily crafted by stuffing extra data into the signatures field in any transaction payload to pad it up to the 1048576 byte limit. 

Although nodes would accept these larger transactions as valid, when it was time to forge them into a block, the additional block headers would make the block size larger than 1048576 bytes. This meant all nodes would reject the block with HTTP error 413 Request Entity Too Large, so the forging node would miss its block and the oversized transactions would remain in the transaction pool, meaning the node would be unable to forge until the oversized transactions expired (the default time being 6 hours).

This could have been used to deliberately target a specific delegate by sending a single transaction to its node that almost hits this limit. The node would not be able to rebroadcast it to other peers because, when a node rebroadcasts transactions to other nodes, a serialized version of the transaction is appended to itself, causing the transaction to exceed the payload size limit so other nodes would not accept it. The result was that only the targeted node had the oversized transaction in its transaction pool, preventing it from forging until the transaction expired. Repeating this prior to the expiry of the oversized transaction would prevent the delegate from ever forging again because its transaction pool would never become empty, unless the delegate node administrator manually cleared their transaction pool - potentially losing other unforged transactions - and even then, an attacker could continue to pollute the transaction pool again afterwards. This vector therefore opened the possibility for individual delegates to be blackmailed.

No delegate requirement

This exploit does not require a delegate or a modified node. Literally anybody can execute it.

>Reported by: delegate fun

## Solution
Mitigation is achieved by enforcing additional checks in the API (transaction pool) as well as on the protocol (consensus) level.

**Patch:** 
https://github.com/ArkEcosystem/core/pull/2097

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.1.2
