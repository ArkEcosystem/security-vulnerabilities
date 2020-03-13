# Plain HTTP connections to the p2p port could crash the node's operating system

**Identifier:** Core-SV-038

## Cause: 
Core did not block any connections to any invalid HTTP paths accessed via the p2p layer's underlying HTTP server, which would never reach the SocketCluster worker or any Core logic at all. This meant a user could send thousands of plain HTTP connections to invalid paths and these connections would remain open, so it was possible to use a cluster of attack nodes to establish hundreds of thousands of connections to use all available file descriptors on a server. This would crash the server completely, since the operating system would no longer be able to open any files.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3537

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.11
