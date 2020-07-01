# ECDSA-signed block and transaction signatures were malleable
**Identifier:** Core-SV-049
## Cause:
Transactions and blocks signed using ECDSA could have their signatures recalculated to generate a new ID for the transactions or blocks, while still remaining cryptographically verified. This could have been used to replay existing transactions on networks where AIP11 was not active, and in all cases, could have been used to repeatedly cause forks by recalculating the signatures of incoming blocks and broadcasting the recalculated blocks onwards, since this would lead to multiple different but valid blocks at the same height on the network.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3806
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.39