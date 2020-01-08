# Sending HyBi WebSocket headers with no data could stop nodes forging

**Identifier:** Core-SV-031

## Cause: 
It was possible to stop a node forging or miss its slot by continually sending payloads containing only a HyBi WebSocket header that signals a data frame, but one that actually contained no data. The effect was that the worker processes hit 100% CPU usage and could not complete their tasks fast enough to keep up with the network.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3331

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.30
