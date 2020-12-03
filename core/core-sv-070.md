# Incoming connections were not banned when failing basic validation checks
**Identifier:** Core-SV-070
## Cause:
Requests to the socket server must adhere to a basic structure containing `data` and `headers` properties, which must be objects nested inside a root `data` object. If the request did not comply with this specification, the connection was terminated but the IP address was not banned. This meant a malicious user could continuously reconnect and keep sending non-conformant requests in a tight loop, using up CPU time.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4176
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.13