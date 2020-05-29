# Second signature transaction replay
**Identifier:** Core-SV-003

## Cause
Attaching a second signature to a previous transaction sent from any wallet that does not have a second passphrase would allow the transaction to be infinitely forged and replayed over and over again.

>Reported by: delegate pierce

## Solution
Ensure that the sender wallet has a second public key and if not reject the transaction.

**Patch:** https://github.com/ArkEcosystem/core/pull/1658

## Status
Closed.

**Release**: https://github.com/ArkEcosystem/core/releases/tag/2.0.16


