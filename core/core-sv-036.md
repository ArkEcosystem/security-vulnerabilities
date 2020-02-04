# Opening thousands of sockets caused high CPU/memory usage and full server crashes

**Identifier:** Core-SV-036

## Cause: 
It was possible for an attacker to open thousands of connections to a node because there was no filtering to prevent multiple connections per originating IP address. Each active connection used a file descriptor in the operating system, and the number of available file descriptors is limited. An attacker could open enough simultaneous connections to use all the available open file descriptors on a node, which would crash it completely, since the operating system was no longer able to open any files.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3404

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.36
