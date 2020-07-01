# Delayed completion of peer verification stopped nodes forging
**Identifier:** Core-SV-048
## Cause:
It was possible to stop delegates from forging by delaying the peer verification process when a node was due to forge. As a forging node enters its slot, it re-verifies its peers by sending a `p2p.peer.getStatus` request to all of its peers. If a peer responds with a higher height than its own height, the node will query that peer further via `p2p.peer.getBlocks` to fetch the block(s) at the higher height to verify they are not forked. A malicious peer could respond with a deliberately higher height and then delay the ensuing response to `p2p.peer.getBlocks` until the forging slot was over, so the peer verification would not complete and the delegate would miss its slot.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3806
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.39