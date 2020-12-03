# Slow query stopped nodes when requesting blocks from specific generators
**Identifier:** Core-SV-072
## Cause:
The `/api/delegates/{delegate}/blocks` endpoint could, in some circumstances, trigger a slow query when requesting a list of blocks. Those requests to this endpoint could be parallelized to overwhelm the database server and prevent the node from responding.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4176
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.13