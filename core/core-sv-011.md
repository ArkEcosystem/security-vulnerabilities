# Malicious delegate 0-ARK transaction spam
**Identifier:** Core-SV-011

## Cause: 
The transaction schema in crypto/validation/rules/models/transactions/transfer is designed to reject transfer (type 0) transactions if the amount is not a positive number. This means that zero-amount type 0 transfers are meant to be invalid, as, indeed, a transaction with an amount of zero is rejected when sent to the /transactions/ endpoint. Since the schema enforces a requirement that the amount must be greater than zero for type 0 transactions, it must be the case that zero amount type 0 transactions are invalid.

However, this check is not enforced at consensus-level. A node operator could remove that schema check and then zero amount transfers will be accepted by their node to be forged. Importantly, due to the lack of consensus-level check, other unmodified nodes will then happily accept blocks containing these forged zero-amount type 0 transactions, storing them in the blockchain, despite being invalid in accordance with the above schema rules. Contrast this with fees, where zero-fee transactions are rejected at consensus-level, so even removing the schema check will result in blocks containing such transactions to be rejected. That is not the case here, although it should be, as it can lead to a situation where delegates can spam the network with zero-amount transfers. If they self-forge the transactions then they recover the fee, so it becomes a completely free way to constantly spam the network with every block they forge, thus bloating the blockchain for all nodes with technically invalid transactions.

>Reported by: delegate fun

## Solution
Mitigation is achieved by enforcing additional checks. 

**Patch:** https://github.com/ArkEcosystem/core/commit/f04fe92b978b7cab536bbe79fc0fb72d022fcd2e

## Status
Closed.
**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.0.18
