# Peer lists could become too large and be manipulated to become a DDoS network
**Identifier:** Core-SV-024

## Cause: 
There was no limit to the number of peers that could be added to peer lists. This could lead to extremely large peer lists being shared across peers which could not be processed in sufficient time, leading to delegates being unable to forge blocks as their nodes would be too busy processing the large amount of peers. Furthermore, if IP addresses of non-Core peers were maliciously added in bulk, this could lead to all legitimate peers being used as an unintentional DDoS network.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/2850

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.14
