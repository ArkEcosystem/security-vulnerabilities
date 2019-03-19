# Public API endpoint open to possible DDOS attack
**Identifier:** Core-SV-014

## Cause: 
Endpoint /api/v2/delegates/{delegate}/voters/balances does not paginate its results. This could be a vector for DDoS as anyone can request the vote balances of every voter of a delegate in one API call. For delegates with large number of voters (>5000) this could overload the server even before the HTTP rate limiting kicked in.

>Reported by: delegate fun

## Solution
API endpoint was removed.

**Patch:** 
https://github.com/ArkEcosystem/core/pull/2265

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.2.2
