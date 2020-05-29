# Marshalled block payloads using the peer-to-peer transport codec were not sanitized
**Identifier:** Core-SV-044
## Cause:
Core 2.6 introduced a new p2p transport codec for blocks, but any payload using this codec was not sanitized properly. The end result was that additional objects could be added to the payload data if the new transport codec was used, which could have been exploited to stop delegates forging by overwhelming their servers with too many concurrent objects. 
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3695
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.37