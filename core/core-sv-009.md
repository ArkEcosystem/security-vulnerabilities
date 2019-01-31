# Fake peers can be added by using non-quad-dotted notation
**Identifier:** Core-SV-009

## Cause: 

The peer list can be filled with fake peers. A similar, but different, issue was reported as Core-SV-004 where the X-Forwarded-For HTTP header could be manipulated to bypass the whitelist to access /internal/ endpoints, and another side effect of that issue was that fake peers in the 127.x.x.x range could be added by hitting any p2p api endpoint with a 127.x.x.x address in the X-Forwarded-For HTTP header. In that case, the fix was to use request.info.remoteAddress as provided by Hapi to get the real IP address of the peer and use that instead.

Peers using non-quad-dotted notation representation can still be added to peer lists, and there are 16,777,214 such addresses (that I am aware of) that are mapped by default to a local loopback address. For example, "localhost" can be added, which will resolve to 127.0.0.1, and any decimal from 2130706433 to 2147483646 inclusive can also be added which will resolve to 127.0.0.1 to 127.255.255.254 respectively, all of which are valid loopback addresses in a standard default Linux installation. This provides a denial of service vector as millions of IPv4 loopback addresses can be added to the peer list which will all resolve to the local node (therefore will be treated as valid) which will overwhelm the server and manifest itself in 3 ways:

1. It prevents the propagation of blocks and transactions to real peers as the node will choke on the fake ones and will not be able to broadcast to the real peers within 8 seconds.
2. Blocks and transactions will be bounced back to the local node up to 16,777,214 times and likely crash the system as it is an internalized denial of service due to resource starvation.
3. Other peers will begin adding the same fake peers to their own peer list as the poisoned peer list gets shared across other peers and this will have a snowball effect as more poisoned peer lists will propagate until eventually everyone has poisoned lists and the entire network grinds to a halt.


>Reported by: delegate fun

## Solution
Use `ipaddr.js` to ensure IPv4 addresses are converted into quad-dotted notation.

**Patch:** https://github.com/ArkEcosystem/core/pull/2042

## Status
Closed.
**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.0.19
