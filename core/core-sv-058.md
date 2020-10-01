# Insufficient transaction asset validation
**Identifier:** Core-SV-058
## Cause:
There was a flaw in the schema validation of incoming transactions which meant an attacker could add additional assets to a multipayment transaction while still passing validation checks. Adding too many of these additional assets would cause delays in parsing the transaction, leading to backlogged requests, IPC timeouts and in the case of delegate nodes, an inability to forge blocks.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/4040
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.57