# Core plugin names were not length restricted so could cause DoS in peer lists
**Identifier:** Core-SV-025

## Cause: 
There was no limit to the length of plugin names returned in peer lists. This could have been used to conduct a bandwidth flood attack by setting up a malicious node to send massive strings as plugin names resulting in overlength peer list responses that could not be processed in time due to their excessive size.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/2875

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.19
