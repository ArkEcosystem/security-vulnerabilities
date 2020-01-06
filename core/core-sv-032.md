# Multiple disconnect JSON packets caused high CPU utilization

**Identifier:** Core-SV-032

## Cause: 
A user could maliciously craft a disconnect JSON packet and constantly send it in a loop to overwhelm a node. As it was a perfectly valid packet, it did not get caught by any of the sanitization checks that were in place, which had the effect of stalling nodes so they could not handle genuine traffic.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3354

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.31
