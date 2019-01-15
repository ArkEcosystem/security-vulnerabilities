# IP spoofing
**Identifier:** Core-SV-0004

## Cause
The whitelist could be bypassed by IP spoofing due to the way we determined the IP of a request. This could also be used to fill up the peer list with loopback IP addresses to cause a DoS attack and prevent block propagation.

>Reported by: delegate fun

## Solution
Use request.info.remoteAddress as provided by Hapi to get an IP of the peer.

**Patch:** https://github.com/ArkEcosystem/core/pull/1658

## Status
Closed.
**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.0.16


