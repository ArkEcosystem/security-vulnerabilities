# P2P endpoint request events were not sanitised
**Identifier:** Core-SV-026

## Cause: 
Spamming nodes with multiple simultaneous requests to invalid websocket endpoints on the peer-to-peer layer with large payload sizes created a memory leak. This killed the socket workers and prevented delegates from forging.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/2875

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.19
