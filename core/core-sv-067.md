# Schema violation requesting common blocks did not close the connection
**Identifier:** Core-SV-067
## Cause:
The `p2p.peer.getCommonBlocks` endpoint schema requires an object containing an array of block ID strings. If the array contained items other than strings, an error was returned to the client but the connection remained open. This allowed a user to keep sending a malicious payload to this endpoint without being banned.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4176
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.13