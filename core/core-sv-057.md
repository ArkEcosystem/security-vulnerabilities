# HTTP header manipulation caused out of memory crashes
**Identifier:** Core-SV-057
## Cause:
It was possible to coerce ARK Core to download any arbitrary file from a remote server by transmitting a HTTP 303 header response to the peer communicator. If the downloaded file was gzip compressed, it was automatically decompressed and stored in memory, potentially expanding to many times its original size. A specially crafted compressed file could grow too large, triggering an out of memory error which would crash the node.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4011
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.54