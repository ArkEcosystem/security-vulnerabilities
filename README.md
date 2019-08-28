![Ark Improvement Proposals](assets/img/header.png)

Producing software inherently comes with risks. All software, especially new releases and large code re-writes, have a higher probability of producing bugs during production and initial release. To combat this, the ARK team has introduced modern testing methods, higher test coverage, a custom developed e2e testing framework and increased the availability for testing on our Development Network prior to the releases. Despite all of that, no one can catch every potential issue. 

We are running our own [development and security bounty program](https://blog.ark.io/ark-development-and-security-bounty-program-a95122d06879), and we have partnered with [Bugcrowd — the planet’s premier crowd sourced security platform!](https://blog.ark.io/ark-and-bugcrowd-go-hunting-cda4025051d5) Make sure to check both bounty programs. Please check detailed instructions, on how to report a security vulnerability https://docs.ark.io/security/.

>This repository series will serve as a public disclosure of any discovered and patched vulnerabilities within the ARK Blockchain Platform Product Landscape (Core, Desktop Wallet, Mobile Wallet, ARK Pay & Deployer).

The lists of know and closed or still open security vulnerabilites can be found in the tables below. The table consists of four fields, describing the basic information about listed security vulnerabilities and links to a more detailed description, by clicking on the link in the identifier field. 

## Core Security Vulnerabilities

| Identifier | Title| Status | Version |
| ------------- | ------------ | ------ | ----- | 
| [Core-SV-026](/core/core-sv-026.md)| P2P endpoint request events were not sanitised | Closed | [v2.5.19](https://github.com/ArkEcosystem/core/releases/tag/2.5.19) |
| [Core-SV-025](/core/core-sv-025.md)| Core plugin names were not length restricted so could cause DoS in peer lists | Closed | [v2.5.19](https://github.com/ArkEcosystem/core/releases/tag/2.5.19) |
| [Core-SV-024](/core/core-sv-024.md)| Peer lists could become too large and be manipulated to become a DDoS network | Closed | [v2.5.14](https://github.com/ArkEcosystem/core/releases/tag/2.5.14) |
| [Core-SV-023](/core/core-sv-023.md)| Peer-to-peer postTransactions endpoint could be spammed to overwhelm nodes | Closed | [v2.5.14](https://github.com/ArkEcosystem/core/releases/tag/2.5.14) |
| [Core-SV-022](/core/core-sv-022.md)| Delegates can be forced to forge empty blocks and genuine transactions can be evicted from the pool | Closed | [v2.4.14](https://github.com/ArkEcosystem/core/releases/tag/2.4.14) |
| [Core-SV-021](/core/core-sv-021.md)| Unverified transactions in bad blocks can purge genuine transactions from the pool | Closed | [v2.4.13](https://github.com/ArkEcosystem/core/releases/tag/2.4.13) |
| [Core-SV-020](/core/core-sv-020.md)| Race condition can result in blocks containing already forged transactions | Closed | [v2.4](https://github.com/ArkEcosystem/core/releases/tag/2.4.0) |
| [Core-SV-019](/core/core-sv-019.md)| Block header manipulation in quorum calculations prevents nodes forging | Closed | [v2.4](https://github.com/ArkEcosystem/core/releases/tag/2.4.0) |
| [Core-SV-018](/core/core-sv-018.md)| Second Signature Transaction Pool Validation | Closed | [v2.4](https://github.com/ArkEcosystem/core/releases/tag/2.4.0) |
| [Core-SV-017](/core/core-sv-017.md)| Second Signature Transaction Broadcast/Sign/Order | Closed | [v2.3](https://github.com/ArkEcosystem/core/releases/tag/2.3.0) |k
| [Core-SV-016](/core/core-sv-016.md)| Receiving a block containing non-valid transactions causes peers to rollback | Closed | [v2.3](https://github.com/ArkEcosystem/core/releases/tag/2.3.0) |
| [Core-SV-015](/core/core-sv-015.md)| Delayed block propagation causes the next delegate to miss its block | Closed | [v2.3](https://github.com/ArkEcosystem/core/releases/tag/2.3.0) |
| [Core-SV-014](/core/core-sv-014.md)| API endpoint open to possible DDOS attack | Closed | [v2.2.2](https://github.com/ArkEcosystem/core/releases/tag/2.2.2) |
| [Core-SV-013](/core/core-sv-013.md)| Transactions near the payload size limit can stop delegates forging | Closed | [v2.1.2](https://github.com/ArkEcosystem/core/releases/tag/2.1.2) |
| [Core-SV-012](/core/core-sv-012.md)| Conflicting delegate registration transactions | Closed | [v2.1.0](https://github.com/ArkEcosystem/core/releases/tag/2.1.0) |
| [Core-SV-011](/core/core-sv-011.md)| Malicious delegate zero(0) - ARK transaction spam | Closed | [v2.0.18](https://github.com/ArkEcosystem/core/releases/tag/2.0.18) |
| [Core-SV-010](/core/core-sv-010.md)| Malicious delegate can cause peers to fork and roll back simultaneously | Closed | [v2.0.19](https://github.com/ArkEcosystem/core/releases/tag/2.0.19) |
| [Core-SV-009](/core/core-sv-009.md)| Fake peers can be added by using non-quad-dotted notation | Closed | [v2.0.19](https://github.com/ArkEcosystem/core/releases/tag/2.0.19) |
| [Core-SV-008](/core/core-sv-008.md)| Forged blocks by anyone can cause the chain to stop/or start recovering | Closed | [v2.0.17](https://github.com/ArkEcosystem/core/releases/tag/2.0.17) |
| [Core-SV-007](/core/core-sv-007.md)| Forging multiple blocks in a slot and rewards hijacking | Closed | [v2.0.17](https://github.com/ArkEcosystem/core/releases/tag/2.0.17) |
| [Core-SV-006](/core/core-sv-006.md)| Transaction replay attack with known 2nd signature passphrase / multisignature | Open | |
| [Core-SV-005](/core/core-sv-005.md)| Double forging a block | Open |  |
| [Core-SV-004](/core/core-sv-004.md)| IP spoofing | Closed | [v2.0.16](https://github.com/ArkEcosystem/core/releases/tag/2.0.16) |
| [Core-SV-003](/core/core-sv-003.md)| Second signature transaction replay  | Closed | [v2.0.16](https://github.com/ArkEcosystem/core/releases/tag/2.0.16) |
| [Core-SV-002](/core/core-sv-002.md)| Generating new Ark using multi signature transaction  | Closed | [v2.0.16](https://github.com/ArkEcosystem/core/releases/tag/2.0.16) |
| [Core-SV-001](/core/core-sv-001.md)| Invalid block received | Closed | [v2.0.16](https://github.com/ArkEcosystem/core/releases/tag/2.0.16) |


## Desktop Wallet Security Vulnerabilities

| Identifier| Title| Status | Version |
| ------------- | ------------ | ------ | ----- | 


## Mobile Wallet Security Vulnerabilities

| Identifier| Title| Status | Version |
| ------------- | ------------ | ------ | ----- | 

## Ark Pay Security Vulnerabilities

| Identifier| Title| Status | Version |
| ------------- | ------------ | ------ | ----- | 

## Ark Deployer Security Vulnerabilities

| Identifier| Title| Status | Version |
| ------------- | ------------ | ------ | ----- | 
