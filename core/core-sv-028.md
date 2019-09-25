# Rate limiting was ineffective due to inappropriate disconnection methods

**Identifier:** Core-SV-028

## Cause: 
Connections that exceeded the rate limit were gracefully disconnected by sending a Forbidden error message to the client, along with a close WebSocket frame. If a node was spammed with requests exceeding the limit, the node workers would reach 100% CPU usage by continually sending these messages and frames back to the client, so they would struggle to cope with genuine requests. This meant that delegates were too resource-starved to forge in time, leading to either missed blocks or delayed blocks on the network.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/2907

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.24
