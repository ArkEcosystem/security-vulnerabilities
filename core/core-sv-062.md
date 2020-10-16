# Outgoing connections were not destroyed after receiving unsupported WebSocket frames
**Identifier:** Core-SV-062
## Cause:
An outgoing socket connection was directly terminated after receiving an unsupported WebSocket frame without notifying the underlying client framework that the connection was deliberately closed. This meant the framework would automatically attempt to reconnect to the peer again, so a malicious user could continue sending more unsupported WebSocket frames in a denial of service attack.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4065
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.1