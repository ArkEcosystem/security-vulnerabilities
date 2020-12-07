# Blocks were accepted but not propagated if received out of slot
**Identifier:** Core-SV-066
## Cause:
A block was only broadcasted onwards to other peers if the current slot time was less than or equal to the block timestamp. This meant it was possible to delay the broadcast of a block until the next slot began so receiving nodes would accept it but not broadcast it further. This could cause significant problems for the network with quorum calculations and overheight block headers.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4176
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.7.13