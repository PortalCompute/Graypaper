---
layout: default
title: Our Technology
nav_order: 2
description: ""
permalink: /technology/our_tech
parent: Technology
---

# Portal's Solution
> Portal's tech stack allows both the privacy problem and the off-chain computational integrity problem to be solved, without the enormous overhead of a pure crypto solution. 

## Trusted Execution Environments (TEEs)
> Portal uses TEEs (Intel SGX) which provide a secure and isolated runtime environment. Sensitive and critical applications are placed inside a tamper-proof `enclave`. 

### Computational Integrity
> Any enclave computation is guaranteed to execute correctly. It is impossible for even host CPU's operating system to edit the contents of the enclave after it has been instantiated. So, even if the host platform has been compromised, enclave's execution will remain unaffected. 

### Remote Attestation
> The process of `remote attestation` guarantees that the enclave is running the expected code and catches all attempts at tampering. The enclave memory is hashed, producing a digest of the initial state, then through an interactive protocol with the hardware manufacturer, an attestation report is generated. This report serves as proof that the enclave was initialized to run the expected program. Any attempts at emulating an enclave are caught during this process. 

> The verification of an attestation proves statement along the lines of `this enclave is indeed running on real TEE-enabled hardware, and its initial state is X and its public key is PK`. The steps for using an enclave would proceed as follows:

> - A program `P` is written in an enclave development environment. During runtime the `P` generates a public keypair `(SK, PK)`. `P` is either public and/or audited, and it is clear that the `SK` is never outputted. 
> - The enclave performs attestation, including the public key `PK` in the report.
> - The user of the enclave verifies both the validity of the report and that `X` is the correct initial state given program `P`.
> - The user communicates inputs to the enclave and triggers the execution of `P`.
> - Upon completion of the computation, the enclave signs off on its outputs using `SK`.
> - The user verifies the signature using `PK`, and if valid, accepts the outputs. 

> In summary, the enclave has proven that it was initialized to run a program `P`, and bound itself to a public keypair `(SK, PK)`. Since only the enclave has access to `SK`, we know that the signed results only could have come from this enclave, which was only capable of running our expected program `P`.

## Confidentiality
> One might be worried that if `SK` is leaked, then incorrect outputs can be signed and passed off as if they were from the enclave. Fortunately, a key property of enclaves is that they are fully private. The enclave memory is encrypted at all times, meaning no one, including the host operating system, can view `SK` or any enclave content.

> This means fully-private computations are possible without the impractical overheads of MPCs. Users can encrypt their inputs such that only the enclave can decrypt it to compute on it, and it is fully customizable whether the outputs are encrypted as well.

## Empowering Smart Contracts
> Like validity proofs, enclaves provide a means to perform off-chain computations that can be verified by smart contracts. More specifically, when an enclave submits the signed results of a computation, the contract verifies the digital signature to ensure that it was signed by the enclave. More detail on the smart contract specifications are [here](). 

> Compared to ZKP based validity proofs, enclaves provide scalability well beyond what is currently possible with more possibilities for privacy. In terms of computational speed, enclaves are most like fraud proofs, but without the inconvenient withdrawal period. When compared to consensus, an enclave can perform a computation cheaper and faster, and without the honest majority assumption; however, as we discuss [here](), consensus protocols can leverage enclaves to increase performance and produce more resilient decentralized oracle networks. 

> The key idea is that any smart contract that needs privacy or extra compute resources can off-load a computation to an enclave, and the results can be cheaply verified back in the contract.




<!-- move this to specialized compute oracle section -->
<!-- ## AI-accelerating Hardware
> On their own, enclaves are ill-equipped for extremely compute intensive AI operations. Training an AI model in a single enclave is akin to training one on your home CPU. Let's just say there's a reason cloud computing companies offer training solutions. 

> Portal solves this by enabling the most compute intensive AI operations to be offloaded to hardware that is better suited for the task (i.e. GPUs, FPGAs, and ASICs). By using the enclave as a secure co-processor, Portal both guarantees the integrity of the fast hardware and that the data remains confidential at every step. 

> For our users, this means they can enjoy the blazing speeds of cloud GPU clusters, while knowing their data and algorithms are always private.  -->



<!-- ## Tech Stack -->
<!-- ![](../gifs/tech_stack.gif) -->