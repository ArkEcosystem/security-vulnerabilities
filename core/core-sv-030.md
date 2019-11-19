# Ping control frame bombardment could prevent block propagation

**Identifier:** Core-SV-030

## Cause: 
Every time a node's WebSocket received a ping control frame, it would reply with a pong control frame. If a node was spammed with ping control frames, the node workers would reach 100% CPU usage by continually sending pong control frames back to the client, so they would struggle to cope with genuine requests. This meant that delegates were too resource-starved to forge in time, leading to either missed blocks or delayed blocks on the network.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3208

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.28
