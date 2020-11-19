# Binary data payloads could stop forging
**Identifier:** Core-SV-064
## Cause:
WebSocket transmissions can be either text or binary, and although Core only uses text messages, there was no filter to block binary payloads in the peer-to-peer layer. It was therefore possible to send binary payloads which would incur large overheads when automatically unmarshalling the binary buffer which would tie up the socket workers to prevent a delegate node from obtaining the correct network state, rendering it unable to forge.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4120
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.6