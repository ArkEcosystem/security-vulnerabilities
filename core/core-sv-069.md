# Exceeding individual but not global rate limit evaded ban
**Identifier:** Core-SV-069
## Cause:
If a request exceeded the rate limit on a specific endpoint, the connection was closed but not blocked. By continually targeting endpoints with restrictive rate limits in this manner, they would never hit the global rate limit which triggers a ban, so they were never blocked. Consequently they could continue connecting and sending more requests to tie up the socket workers to ultimately stop a node from functioning correctly.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4176
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.13