# Externally hitting internal P2P endpoints could stop a node handling requests

**Identifier:** Core-SV-029

## Cause: 
Accessing an internal endpoint from an external unauthorized connection would send an Unauthorized error message to the client, but the socket would still be connected. As the connection remained open, in certain circumstances it was possible to trigger a node to continually send Unauthorized messages to block its workers so they could no longer process legitimate requests.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/2945

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.25
