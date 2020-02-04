# A malicious block containing thousands of transactions could take down a node

**Identifier:** Core-SV-037

## Cause: 
A malicious user could keep sending bad blocks containing thousands of transactions inside them. As all the transactions inside the blocks were verified and validated, this maxed out the CPU usage and prevented nodes from operating correctly. It did not matter that the block itself failed verification or had a fake generator, as all transactions inside the block were still verified and validated. Since there were many thousands of transactions stuffed into the block, this CPU intensive process took too long to complete and the rate limiter did not prevent the attack since the rate limit was reset long before the process finally finished, so an attacker could continue indefinitely to keep a node offline.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3404

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.36
