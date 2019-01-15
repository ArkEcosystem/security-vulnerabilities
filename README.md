![Ark Improvement Proposals](assets/img/header.png)

Producing software inherently comes with risks. All software, especially new releases and large code re-writes, have a higher probability of producing bugs during production and initial release. To combat this, the ARK team has introduced modern testing methods, higher test coverage, a custom developed e2e testing framework and increased the availability for testing on our Development Network prior to the releases. Despite all of that, no one can catch every potential issue. 

>This repository series will serve as a public disclosure of any discovered and patched vulnerabilities within the ARK Blockchain Platform Product Landscape (Core, Desktop Wallet, Mobile Wallet, ARK Pay & Deployer).

The lists of know and closed or still open security vulnerabiliters can be found in the tables below. The table consits of four fields, describing the basic information about listed security vulnerabilties and links to a more detailed description.

## Core Security Vulnerabilities

| Identifier        | Title        | Status | Version |
| ------------- | ------------ | ------ | ----- | 
| [Core-SV-2019-0007](/core/core-sv-2019-0007.md)|  Forged blocks by anyone can cause the chain to stop/or start recovering | Closed | [v2.0.17](https://github.com/ArkEcosystem/core/releases/tag/2.0.17) |
| [Core-SV-2019-0008](/core/core-sv-2019-0008.md)|  Forging multiple blocks in a slot and rewards hijacking | Closed | [v2.0.17](https://github.com/ArkEcosystem/core/releases/tag/2.0.17) |
| [Core-SV-2019-0006](/core/core-sv-2019-0006.md)|  Transaction replay attack with known 2nd signature passphrase / multisignature | Open | |
| [Core-SV-2019-0005](/core/core-sv-2019-0005.md)|  Double forging a block | Open |  |
| [Core-SV-2019-0004](/core/core-sv-2019-0004.md)|  IP spoofing | Closed | [v2.0.16](https://github.com/ArkEcosystem/core/releases/tag/2.0.16) |
| [Core-SV-2019-0003](/core/core-sv-2019-0003.md)|  Second signature transaction replay  | Closed | [v2.0.16](https://github.com/ArkEcosystem/core/releases/tag/2.0.16) |
| [Core-SV-2019-0002](/core/core-sv-2019-0002.md)|  Generating new Ark using multi signature transaction  | Closed | [v2.0.16](https://github.com/ArkEcosystem/core/releases/tag/2.0.16) |
| [Core-SV-2019-0001](/core/core-sv-2019-0001.md)|  Invalid block received | Closed | [v2.0.16](https://github.com/ArkEcosystem/core/releases/tag/2.0.16) |
