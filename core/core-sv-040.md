# Long-lived HTTP requests via the P2P layer could crash the node

**Identifier:** Core-SV-040

## Cause: 

It was possible to bombard a peer with long-lived HTTP requests by opening a connection to the correct /socketcluster/ path, but never upgrading the connection to a WebSocket. This connection could have been kept alive by sending a HTTP header every second (e.g. Host: X.X.X.X over and over again in a 1 second loop) and never sending the Upgrade: websocket or Connection: upgrade headers. The consequence of this was the ability to overload the server with open TCP sockets that are never established as WebSockets (so rate limit protections never kick in), once again leading to a situation where an attacker could spawn thousands of connections to use up all the node's file descriptors to crash the underlying operating system.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3596

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.27
