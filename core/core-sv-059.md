# Newly connected peers did not have an initial maximum payload limit
**Identifier:** Core-SV-059
## Cause:
Core dynamically adjusts the maximum payload size of a peer's response depending on the type of request being made to the peer, however it did not set a default maximum payload size when initially establishing a connection to a peer. This allowed an attacker to send a very large payload as soon as the connection was opened prior to any request being made, which would crash Core by causing an out of memory condition.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4040
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.57