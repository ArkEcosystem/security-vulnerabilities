# Conflicting delegate registration transactions not detected by the transaction guard
**Identifier:** Core-SV-012

## Cause: 
A user could POST to the /transactions/ API endpoint either: 
- one payload of two or more transactions containing delegate registrations for the same username but from different wallets; or 
- a single transaction containing a delegate registration for a username, immediately followed by another transaction containing a delegate registration for the same username but from a different wallet, and this could be repeated numerous times prior to the first delegate registration transaction being forged in a block.

All of these transactions would be accepted, added the pool and broadcasted to other peers to be added to their pools too. The next forging delegate would then miss its block because the forged block would contain multiple delegate registration transactions for the same username, which would be rejected as it would fail to apply the second delegate registration onwards since the username would be already taken by the first delegate registration so the entire block would be rejected as invalid. As the conflicting transactions were broadcasted to all peers but not forged, they remained in their respective transaction pools, so the next delegate in line would attempt to forge them again with the same outcome, and this would have a cascading effect, resulting in a stalled network because no delegate would be able to forge a valid block as they'd all try to forge blocks containing the conflicting transactions. If exploited maliciously, any bad actor could have stalled the network permanently by repeatedly sending conflicting transactions to ensure the transaction pools were never clean so the network could not recover.

This exploit does not require a delegate, malicious or otherwise, to carry it out. It can be triggered by any user of the network at any time, either deliberately or accidentally.

>Reported by: delegate fun

## Solution
Mitigation is achieved by enforcing additional checks in the API (transaction pool) as well as on the protocol (consensus) level.

**Patch:** 
https://github.com/ArkEcosystem/core/pull/2080

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.1.0
