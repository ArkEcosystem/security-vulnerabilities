# Reviver function in the transport codec could cause denial of service
**Identifier:** Core-SV-071
## Cause:
Every message that is sent or received over the peer to peer protocol is processed by a custom codec. Part of the decoding process in that codec attempts to parse the received message string with a reviver function. If that function failed for any reason, the rate limiter was not triggered, so a malicious user could execute a denial of service attack by continually and uninterruptedly sending payloads that caused the reviver function to fail.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4176
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.13