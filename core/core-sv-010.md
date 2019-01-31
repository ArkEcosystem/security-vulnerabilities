# Malicious delegate can cause peers to fork and roll back simultaneously
**Identifier:** Core-SV-010

## Cause: 
A malicious delegate can craft a block at the correct height but with a timestamp from a previous round that collides with a valid forging slot time for that delegate in the current round. This has the result that the block will be initially accepted and will not be flagged up as an incorrect generator because the timestamp is technically valid for the forging delegate in the current slot. However, because the block is unchained due to the incorrect timestamp, it will cause the receiving node to immediately enter fork recovery mode and roll back the chain.

The severity of this issue is the fact that all nodes receiving the bad block will fork and immediately roll back, which could trigger a perfect storm if every node on the network rolls back at the same time, erasing the latest blocks, meaning no node has the latest blocks to recover from anymore. This is easy to achieve with a modified forger by requesting the IP addresses of the peers of all your own peers, continually iterating until you obtain an exhaustive list of all IPs on the network and then blast a bad block to all of those IPs at the same time across multiple nodes to reduce latency. Although transactions in those destroyed blocks would in theory return to the pool to be re-forged, the problem is that, over time, nodes stop responding and require manual intervention to recover from this attack and it could take longer than the transaction expiry time for the network to start moving again to re-forge them.

>Reported by: delegate fun

## Solution
Mitigation is achieved by discarding blocks with a past timestamp without triggering the fork recovery process.

**Patch:** https://github.com/ArkEcosystem/core/pull/2042

## Status
Closed.
**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.0.19
