# Transaction replay attack with known 2nd signature passphrase / multisignature
**Identifier:** Core-SV-0006

## Cause
It is currently possible to generate distinct signatures for the same transaction from the same private key which can all be verified by the same public key. The 2nd signature changes the ID of a transaction so it is not considered to be a duplicate, but a new transaction. That means if your second passphrase is lost/stolen an attacker can replay your previous transactions by simply changing the 2nd signature.

>Reported by: delegate pierce

## Solution
An AIP to address this is in progress and we have started evaluating the best possible solution to address this. This means a hard fork at some milestone level and a mitigation script for transactions prior to the included milestone. When the AIP is finalized — we will share it with everyone, as always. Until then — keep your passphrase safe and do NOT share it with anyone (even if it is just the 2nd one)! Utilizing the 2nd signature with a 2nd party as a form of multi-signature was never the intended use of the 2nd signature and as per the above, can lead to theft or misuse of funds.

**Patch:** TBD
**Work In Progress:** TBD 

## Status
Open.
**Release:** TBD
