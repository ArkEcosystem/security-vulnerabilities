# Forged blocks by anyone can cause the chain to stop/or start recovering
**Identifier:** Core-SV-008

## Cause
Anyone is able to broadcast signed blocks. When receiving a forged block from a wrong generator, the chain will fork. This also applies to inactive (unknown) generators. If a malicious actor now keeps broadcasting such blocks, the chain would effectively cease operating.

>Reported by: delegate fun

## Solution
 When the wrong generator is detected, distinguish between inactive and active generators and only fork in the latter case. Otherwise the block will be just ignored.

**Patch:** https://github.com/ArkEcosystem/core/pull/1974/

## Status
Closed.
**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.0.17
