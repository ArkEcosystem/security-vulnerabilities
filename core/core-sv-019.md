# Block header manipulation in quorum calculations prevents nodes forging
**Identifier:** Core-SV-019

## Cause
Forging nodes can be tricked into thinking they are double forging, even when they are not. This activates the automatic protection which stops the nodes from forging. As the delegates were not actually double forging in the first place, they do not produce any blocks. If all delegates are targeted, the chain completely stops.

>Reported by: [alessio](https://github.com/alessiodf)

## Solution

**Patch:**

- https://github.com/ArkEcosystem/core/pull/2686
- https://github.com/ArkEcosystem/core/pull/2687

## Status
Closed.

**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.4.0