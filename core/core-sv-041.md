# Overloading the public API could stop the transaction and block processing on a node

**Identifier:** Core-SV-041

## Cause: 

The public API could have been overloaded to stop a node from processing any incoming transactions or blocks by opening simultaneous requests to the /api/blocks or /api/transactions endpoints.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3605

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.30
