# Port ping payload sizes were unchecked and could cause bandwidth flood attacks
**Identifier:** Core-SV-052
## Cause:
It was possible to craft a malicious HTTP GET response to the peer communicator to redirect traffic to a third party server. This could have been used, among other possibilities, to download very large multi-gigabyte files to consume all the bandwidth of a node.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3905
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.49