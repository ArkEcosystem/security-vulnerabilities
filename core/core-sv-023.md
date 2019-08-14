# Peer-to-peer postTransactions endpoint could be spammed to overwhelm nodes
**Identifier:** Core-SV-023

## Cause: 
The `postTransactions` peer-to-peer websocket endpoint could be spammed with bundles of invalid or expired transactions. The cryptographic process of verifying all those transactions would overwhelm a node to prevent it from being able to keep up with the network. It would stop receiving blocks and delegates would be unable to forge. Since the spam transactions were invalid or expired, they would never be forged.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/2848

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.14
