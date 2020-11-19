# Large payloads sent to internal endpoints prevented forging
**Identifier:** Core-SV-063
## Cause:
There is no schema validation for incoming data received on most of the internal peer-to-peer endpoints, so a malicious user could send a large JSON payload to any of these endpoints which is time consuming to parse. Although the connection would be terminated because the user was not authorized to access the endpoint, the associated IP address would not be banned, so a bad actor could keep reconnecting and sending this payload in a loop which would jam the socket server worker processes above 100% CPU usage.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4120
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.6