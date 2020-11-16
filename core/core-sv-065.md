# Requesting blocks at a very high height locked up PostgreSQL
**Identifier:** Core-SV-065
## Cause:
The PostgreSQL process could be jammed at 100% CPU usage across multiple cores by requesting one or more blocks from a node starting at an exceptionally high height. This request took longer to complete than the rate limit of once every 2 seconds for the relevant endpoint, so a bad actor could keep sending these requests constantly to lock up PostgreSQL at 100% CPU usage across multiple cores.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4120
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.6