# Broadcasting invalid WebSocket opcodes caused significant network degradation and missed blocks

**Identifier:** Core-SV-035

## Cause: 
Sending malformed WebSocket packets with reserved or unimplemented opcodes would trigger the socket's onerror event handler, but Core did not listen for this event and the connection was not blocked. The process of repeatedly throwing the error was sufficiently computationally expensive that it was possible to take down a node and stop it forging by sending a constant stream of malformed packets.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3404

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.36
