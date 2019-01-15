## Title or name of the Security Vulnerability 
The numbers are following the format: CODE-SV-NNN (e.g. CORE-SV-000). The code field prefix defines the product to which the security vulnerability applies. We support the following CODE prefixes:
- Core - for Ark Core
- Dewa - for Desktop Wallet
- Mowa - for Mobile Wallet
- Pay - for Ark Pay
- Depl - for Ark Deployer

The first line after the title should be the security vulnerability identifier.
**Identifier**: Core-SV-0000

## Cause
Describe the cause of the security vulnerability by explaining the reasons, steps or process on how to reproduce it.
The cause can also include the reporter contact details if allowed to disclose them publicly. For example:
>Reported by: Name Surname, email, github link

## Solution
Explaination on how to mitigate the security vulnerability. Explanation should provide detailed steps.

**Patch:** https://github.com/ArkEcosystem/core/pull/1692

## Status
Status can be Open/Closed, where closed means that the security vulnerability is mitigated and represents not an actual threat.
Also include date and version information in the form of the github release link.
**Release:** https://github.com/ArkEcosystem/core/releases/tag/2.0.16