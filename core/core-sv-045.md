# Induced slow block propagation forked the network
**Identifier:** Core-SV-045
## Cause:
Specially crafted payloads could be constructed to target either the public API or the peer-to-peer layer which would cause a delegate to delay sending its newly forged block until the next forging slot. This could cause a whole network fork since it would result in two conflicting blocks being propagated at the same height.
>Reported by: [alessio](https://github.com/alessiodf)
## Solution
**Patch:** https://github.com/ArkEcosystem/core/pull/3746
## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.6.38