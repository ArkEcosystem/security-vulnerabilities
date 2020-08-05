# Negative values were erroneously accepted in ECDSA signatures
**Identifier:** Core-SV-055
## Cause:
Core did not check for negative values in the R or S components of ECDSA signatures, which are not allowed in the specification. This meant that it was possible to maliciously modify an existing valid signature to include negative values for either R or S and this signature would still erroneously verify as true, since the values were internally normalized as positive integers. However, by doing so, the block or transaction would have a different ID, potentially leading to transaction replay on non-AIP11 networks or network forks due to conflicting blocks being propagated at the same height.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3905
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.49