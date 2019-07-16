# Delegates can be forced to forge empty blocks and genuine transactions can be evicted from the pool
**Identifier:** Core-SV-022

## Cause: 
Unforgeable transactions could fill the transaction pool to prevent genuine transactions being forged as the forging process would retrieve transactions up to the maximum transactions per block size, filter away the invalid ones and return the result. This could possibly return zero valid transactions after filtering if the transaction pool contained more than the maximum number of transactions per block of unforgeable transactions with a higher fee than the genuine transactions. Additionally, sending a high volume of these invalid transactions could evict genuine transactions from the transaction pool at zero cost to an attacker.  

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/2766

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.4.14

