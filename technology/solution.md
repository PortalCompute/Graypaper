---
layout: default
title: Our Technology
nav_order: 2
description: ""
permalink: /technology/our_tech
parent: Technology
---

# Portal's Solution
> Portal's tech stack allows both the privacy problem and the off-chain computational integrity problem to be solved without the enormous overhead of a pure crypto solution. 

## Trusted Execution Environments (TEEs)
> Portal uses TEEs (Intel SGX), which provide a secure and isolated runtime environment. Sensitive and critical applications are placed inside a tamper-proof `enclave`. 

### Computational Integrity
> Any enclave computation is guaranteed to execute correctly. Even the host CPU's operating system cannot edit the contents of the enclave after it has been instantiated. So, even a compromised host will be unable to affect an enclave's execution. 

### Remote Attestation
> The verification of an attestation proves the statement: `this enclave is indeed running on real TEE-enabled hardware, and its initial state is X, and its public key is PK`. The steps for using an enclave would proceed as follows:

> - A program `P` is written in an enclave development environment. `P` generates a public keypair `(SK, PK)` during runtime. `P` may be public, audited, or both, and it is evident to any observer that `P` never leaks `SK`.

> - The enclave performs attestation, including the public key `PK` as part of the attestation report.
> - The enclave user verifies both the validity of the report and that `X` is the correct initial state given program `P`.
> - The user communicates inputs to the enclave and triggers the execution of `P`.
> - Upon completion of the computation, the enclave signs off on its outputs using `SK`.
> - The user verifies the signature using `PK` and accepts the outputs if valid. 

> In summary, the enclave has proven that it was initialized to run a program `P`, and bound itself to a public keypair `(SK, PK)`. Since only the enclave has access to `SK` and the code was audited to never reveal `SK`, we know that the signed results could only have come from this enclave, which was only capable of running our expected program `P`.

## Confidentiality
> One might be worried that if `SK` is leaked, then incorrect outputs can be signed and passed off as if they were from the enclave. Fortunately, a fundamental property of enclaves is that they are entirely private. The enclave memory is encrypted at all times, meaning no one, including the host operating system, can view `SK` or any enclave content.

> This means fully-private computations are possible without the impractical overheads of MPCs. Users can encrypt their inputs such that only the enclave can decrypt them to compute, and it is fully customizable whether the outputs are encrypted.

## Empowering Smart Contracts
> Like validity proofs, enclaves provide a means to perform off-chain computations that smart contracts can verify. More specifically, when an enclave submits the signed results of a computation, the contract verifies the digital signature to ensure that the enclave signed it. 

> Compared to ZKP-based validity proofs, enclaves provide scalability well beyond what is currently possible, with more possibilities for privacy. In terms of performance, enclaves are most like fraud proofs, but without the inconvenient withdrawal period. When compared to consensus, an enclave can perform a cheaper and faster computation without the honest majority assumption.

> The key idea is that any smart contract that needs privacy or extra compute resources can offload computations to an enclave. The results can be cheaply verified back in the contract.

