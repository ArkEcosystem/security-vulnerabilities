# Unverified transactions in bad blocks can purge genuine transactions from the pool
**Identifier:** Core-SV-021

## Cause: 
When a block was rejected for failing verification, any transactions from the sender(s) of any transactions in the block were purged from the transaction pool, even if they failed verification. This meant anybody could create a bad unverified block containing fake transactions to delete genuine transactions from that wallet from the transaction pool.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/2751

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.4.13
