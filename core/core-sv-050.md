# Consecutive big blocks could exceed the maximum payload limit
**Identifier:** Core-SV-050
## Cause:
By repeatedly sending large transactions to fill consecutive blocks, it was possible to exceed the maximum permitted client-side payload limit for any WebSocket connection. This would trigger peer bans when trying to download a batch of blocks that exceeded this payload size and meant no new nodes could ever join the network as they would not be able to download a batch of blocks exceeding this limit, thus preventing any new relays from syncing with the network.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3905
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.49