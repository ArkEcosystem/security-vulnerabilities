# Automatic peer reconnection did not reattach socket event listeners
**Identifier:** Core-SV-068
## Cause:
When a new outbound connection is made by the peer connector, Core adds event listeners to the underlying socket to handle errors, abnormal packets and rate limiting. However, these listeners were only added to the initial socket that was created for the connection. If the connection was lost which triggered an automatic reconnection, a new socket was created without these event listeners.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4176
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.13