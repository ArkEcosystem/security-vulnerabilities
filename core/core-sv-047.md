# Block ID-based exceptions were vulnerable to preimage attacks and blockchain poisoning
**Identifier:** Core-SV-047
## Cause:
Block IDs can be added as exceptions which are accepted even if they fail verification but there was no check to ensure the correct transactions were inside the excepted blocks. This meant that transactions could be mutated or changed entirely inside of excepted blocks and the node would still accept them since it no longer mattered that the block would not pass verification checks.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3806
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.39