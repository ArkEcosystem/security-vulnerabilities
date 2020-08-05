# Slow PostgreSQL query attack could have caused delegates to miss blocks
**Identifier:** Core-SV-051
## Cause:
Filling enough blocks with transactions to make a large cumulative payload and then repeatedly calling `p2p.peer.getBlocks` to download that set of blocks from multiple IP addresses at the same time every second could make any forging node miss blocks. This was because of a slow query which took too long to complete in those circumstances, which caused significantly elevated CPU usage on the main process. This could quickly amplify as new requests could be made before all the previous ones were completed, continually stacking more requests on top of the existing ones until the database was overwhelmed.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3905
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.49