# Outgoing sockets were not properly rate limited
**Identifier:** Core-SV-060
## Cause:
Although incoming sockets were properly rate limited, outgoing sockets were not, as the only rate limit applied to outgoing sockets was for internal ping messages. Once Core made an outgoing connection to a malicious peer, that peer could continually send packets of data to overwhelm the node, as long as the data was anything other than an internal ping message.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4054
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.0