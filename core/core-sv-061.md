# Peer lists could exceed the maximum permitted payload size
**Identifier:** Core-SV-061
## Cause:
P2P peer lists contained data about the plugins each peer was running. This meant a malicious user was able to construct a swarm of peers all configured with multiple plugins so the cumulative size of peer lists would grow to exceed the maximum permitted size of 102400 bytes. This would prevent any node from receiving an updated peer list, stopping new nodes from joining the network and would disconnect existing ones when receiving an oversized peer list.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4054
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.0