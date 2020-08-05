# DER signature manipulation could fork the network, roll back and replay transactions
**Identifier:** Core-SV-054
## Cause:
Blocks and transactions signed with DER encoded signatures could be manipulated by appending extra data to the end of the signature outside of the R and S values. This meant the transactions and blocks were still cryptographically valid but would have a different ID, allowing for transaction replay on non-AIP11 networks and to persistently fork the network by propagating different blocks at the same height.  
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3905
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.49