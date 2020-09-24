# Prepending zeros in the hex representation of a signature would change its ID
**Identifier:** Core-SV-056
## Cause:
For the purpose of cryptographic verification, R and S components of ECDSA signatures are integers, but the hashing process used by Core to calculate the ID of a transaction or block uses their byte sequence instead. Core did not check for the presence of extra zeros at the start of either the R or S components of a signature, so prepending extra zeros to either component would change the ID of any block or transaction since this would modify the byte sequence, while remaining cryptographically verified as the extra zeros were ignored during verification since that process uses the integer values instead. This meant transactions could have been replayed on non-AIP11 networks since they would have had new IDs, and it could have also led to forking of the network if multiple blocks were propagated at the same height with different block IDs.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3905
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.52