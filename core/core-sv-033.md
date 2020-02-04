# JSON payloads with too many key-value pairs were too CPU intensive to parse

**Identifier:** Core-SV-033

## Cause: 
There was a Denial of Service security vulnerability inside the P2P layer which could be triggered by sending valid JSON strings to valid endpoints, but where the JSON string contained too many key-value pairs. This was too time consuming to parse, so a node was unable to process other business, leading to missed blocks and an inability to forge.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:** https://github.com/ArkEcosystem/core/pull/3404

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.5.36
