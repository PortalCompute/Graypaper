---
layout: default
title: Specialized Compute Oracle Networks
nav_order: 2
parent: Services
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
permalink: /technology/services/special_compute
grand_parent: Technology
---

# Specialized Portal Compute Oracle Network 
> Unlike L1 blockchains, *PCONs* are flexible in their implementations, and *PCBs* can be implemented per-computation to optimize performance and efficiency. A [*G-PCON*](https://graypaper.portalcompute.com/technology/services/general_compute) can, in theory, run any computation, making it a convenient target for developers. However, since the node must emulate the execution of a program, it will always perform slower than running the program natively.

> For example, including a VRF function inside the *PCB* means that the code is compiled directly as part of the enclave binary. This function will be much faster than executing the equivalent logic via a generic runtime (e.g. a VRF Python function executed via Python interpreter).

> For certain computations, the cost of emulation can be prohibitive. For the sake of performance, more efficient implementations are necessary. This is akin to why dedicated hardware (i.e. FPGAs and ASICs) are necessary to compete in proof-of-work. Your home laptop/desktop CPU designed for general purpose computing will be orders of magnitude slower than a custom hardware solution.

> Described below are instantiations of *PCONs* that target specific computations. 

# AI Services
> The past decade has shown that two trends are apparent. AI will only continue to integrate into our lives, and the way we use and train AI is currently flawed. At Portal Compute, we strongly believe that blockchains are an essential tool for solving the systemic issues around trust and transparency with AI.

> Specialized *PCONs* can be implemented such that the nodes utilize both TEEs and AI-specialized hardware (GPU, FPGAs, and ASICs) for machine learning at scale. By using the enclave as a secure co-processor, Portal guarantees the integrity of the fast hardware and that the data remains confidential at every step. While achieving these two properties through different approaches (i.e. MPCs or pure TEEs) is possible, they will be orders of magnitude slower.

## Verifiable Inference
> ![Verifiable Inference Flow](../../gifs/inference_flow_v2.gif)
> Portal's AI oracle services allow users to request inference on their data from an off-chain machine learning model via an `Inference OIC`. The user can be any entity that accesses a smart contract, including individual users, other smart contracts, DAOs, Dapps, IOT devices, etc.

> Both the user's input and the machine learning model are end-to-end encrypted such that only the *PCON* can decrypt them in the secure enclave. This confidentiality means users can get value from AI without relinquishing custody of their data, and model owners can monetize their AI without the threat of losing IP. 



## Verifiable Training
> Portal’s AI oracle services allow users to train machine learning models within a *PCON*. The model owner uploads an encrypted model such that only the *PCON* can decrypt it. 

> This owner could be an individual, DAO, Dapp, etc. This entity specifies in the `Training OIC` who is allowed to train this model. Whitelisted entities can submit [encrypted] datasets to the *Training OIC*. The *PCON* will verifiably train the model with the dataset and then fulfill the request with a pointer to the updated model (stored in decentralized storage like IPFS).

> To ensure the continuity of the model's history, the contract will automatically reject a new model pointer if the *PCON* fails to produce proof that it was produced from the expected input model and dataset.

>### A tamper-proof history
>>![Model Lineage](../../gifs/training_flow_2.gif)
>> Whenever the *PCON* fulfills a training request, an immutable log is recorded on the blockchain. This history enables users to track the lineage of their models, monitor performance, diagnose issues, and even receive audits. 

## Data Preprocessing 
> ![Verifiable Data Preprocessing Flow](../../gifs/preprocessing_flow_v2.gif)
> It is common to have many stages to clean, label, and augment data before using it to train a model. Portal enables these stages to be performed confidentially and with integrity via AI oracle requests. 

> Portal offers a spectrum of data preprocessing services that can be requested via `Data Preprocessing OIC`. Users can perform single-stage requests (i.e. ```label()```) or can perform many at once via a multi-stage request as illustrated above.  

> At any stage in the preprocessing pipeline, the partially processed data (or fully synthetic data) is capable of being sold to data marketplaces.



<!-- # VRF -->