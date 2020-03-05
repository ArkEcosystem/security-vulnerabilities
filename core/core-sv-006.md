# Transaction replay attack with known 2nd signature passphrase / multi-signature
**Identifier:** Core-SV-006

## Cause
It is possible to generate distinct signatures for the same transaction from the same private key which can all be verified by the same public key. The 2nd signature changes the ID of a transaction so it is not considered to be a duplicate, but a new transaction. Prior to the introduction of nonces in Core 2.6, if your second passphrase was lost/stolen an attacker could replay your previous transactions by simply changing the 2nd signature.

>Reported by: delegate pierce

## Solution
A new transaction format was introduced in Core 2.6 that utilizes a signed incremental nonce value which can never be reused. This prevents transaction replay even if the ID of the transaction changes, since the nonce value will already be used by the original transaction.

**Patch:** https://github.com/ArkEcosystem/core/pull/2573

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.0

