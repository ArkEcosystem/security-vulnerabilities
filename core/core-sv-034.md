# Unhandled unemitted events could trigger high CPU spikes and propagation delays

**Identifier:** Core-SV-034

## Cause: 
Core only incremented the rate limiter when the SocketCluster emit event was fired, but there were some circumstances where specially crafted payloads would not trigger this event. This meant that anyone could flood a node with such messages which did not increment the rate limiter.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3404

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.36
