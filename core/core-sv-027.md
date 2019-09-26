# Malformed messages on the P2P layer could hang up a node and stop delegates forging

**Identifier:** Core-SV-027

## Cause: 
It was possible to take down a node and either stop it forging or delay its block propagation to fork the network by exploiting a weakness in SocketCluster by sending raw payloads to the node that did not conform to the SocketCluster JSON format.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/2907

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.24
