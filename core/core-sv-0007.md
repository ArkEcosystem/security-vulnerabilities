# Forging multiple blocks in a slot and rewards hijacking - Core-SV-2019-0007

## Cause
Any active delegate can forge multiple blocks within their allocated 8 second slot time, as long as the block IDs are different and are all sent to the same node with an incrementing block height (last block height + 1), as each block is considered to be valid and accepted on the chain. This has the effect of generating block rewards for each of the multiple blocks that are forged in the slot, resulting in inflated rewards per round for any delegate that carries out this exploit.

This attack requires an active delegate to carry it out, since you need to have a valid slot in which to perform the exploit and inactive delegates won't have a valid slot. 

>Reported by: delegate fun

## Solution
Additionally check the slot number of a received block, which must now be greater than the previous (lower) slot number. This way it is guaranteed that only 1 block per slot can be forged.

> Patch: https://github.com/ArkEcosystem/core/pull/1974/

## Status
Closed.
> Release link: https://github.com/ArkEcosystem/core/releases/tag/2.0.17
