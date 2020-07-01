# Block schema violations could halt the blockchain
**Identifier:** Core-SV-046
## Cause:
It was possible to stop a node from receiving new blocks by sending a single block to it via `p2p.peer.postBlock` which contained a chained block header with a `numberOfTransactions` value greater than 0 but where no transactions were included in the block. This caused an error to be thrown which stopped the processing queue indefinitely.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3806
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.39