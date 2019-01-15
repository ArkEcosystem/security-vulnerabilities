# Invalid block received - Core-SV-2019-0001

## Cause
The lastDownloadedBlock variable was not reset when discarding invalid blocks. This caused network nodes to continually attempt to download new blocks from the wrong height, effectively halting the network. This issue would have allowed a malicious user to disrupt network nodes and the network itself.

>Reported by: delegate fun

## Solution
Reset last downloaded block after discarding an invalid block.

> Patch: https://github.com/ArkEcosystem/core/pull/1692

## Status
Closed.
> Release link: https://github.com/ArkEcosystem/core/releases/tag/2.0.16


