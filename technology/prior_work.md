---
layout: default
title: Prior Work
nav_order: 3
description: ""
permalink: /technology/prior_work
parent: Technology
---

# Layer-1 Privacy Networks
> There are a number of Layer-1 blockchains that leverage Trusted Execution Environments. These networks can offer privacy preserving smart contracts that are executed within secure enclaves. This privacy-first mentality sets a precedence for the future of blockchains and smart contracts. Dapps that are built on top of these networks immediately inherit privacy-preserving properties, offering a new paradigm, where data can remain in the custody of users. This unlocks entirely new use-cases that were previously inaccessible including private markets, games, storage, and even healthcare. 

## Limitations
> While these networks have set an amazing foundation to solve the privacy problem, there still are reasons why we aren't seeing large computations (i.e. modern-sized AI workloads) running on top of any of these networks in practice today. 

### Consensus
> Consensus is required for the network to agree on the next state of the blockchain. Like their non-private counterparts, these L1 privacy networks require a reasonable gas-limit in order to reach finality without sacrificing throughput. 

> Imagine a scenario where a user on one of these L1s wants to train a large deep learning model, and the network's gas-limit allows for this. We can conservatively estimate that will take ~1 week for a node to complete training, although likely *much* longer without AI-specialized hardware. 

> One can see how this could be problematic for the L1's throughput. By taking on this compute-intensive training job, the node is effectively denying itself from processing any other transactions for the next week.

### Generality
> Privacy-preserving L1s support general purpose smart contracts to best facilitate development on their network. A Turing Complete programming language would in theory allow a developer to deploy any application on the network. However, in practice, there are some applications necessitate more efficient runtimes (i.e. specialized hardware) to be practical.  

> Again, assuming the L1's gas-limit is high enough to train a deep learning model, the required time would be unreasonable. For example, training OpenAI's GPT3 would require [**355 years**](https://lambdalabs.com/blog/demystifying-gpt-3/) when trained on a single instance of the market's fastest GPU.

> To put this into perspective, this will be *much* faster than training on a TEE which is akin to training on your home CPU. Also, since the training logic is programmed into a general purpose smart contract, performance will be even worse than running a native CPU program. The only reason large models like GPT3 exists today is because they used *many* GPUs to train it in parallel.

> Assuming specialized compute outperforms general compute in terms of speed and cost for certain applications, then L1s that offer general purpose smart contracts will underperform compared to L1s that specialize. 

> For example, we can focus on one specific computation: matrix multiplication. A theoretical L1 with GPU-equipped nodes can perform this specific computation orders of magnitude faster than a general purpose L1 running the same computation inside of a smart contract. It is possible for the general purpose L1 can hard-fork to compete, but this is irrational.

> This example begs the question: are specialized chains necessary to support specialized computation? We think the answer is no, and that this should be discouraged for two reasons:

> First, any new chain will require network effects to grow. Without sufficient participation, the underlying security of the chain can be compromised (i.e. 51% attack). Second, the existence of one chain per specialized computation poses an interoperability nightmare.

## Summary
> Existing privacy-preserving L1s are limitted in their compute power due to the reliance on consensus. By supporting general purpose computation, they make it easy for developers, but inevitably underperform for compute intensive applications. Additionally, in order to leverage the privacy-preserving tech, developers are required to develop on top of the L1 using SDKs. This means existing Dapps on other L1s are unable to benefit from this privacy-preserving tech.

## Portal's answer
> Portal is a chain-agnostic oracle service to bring privacy-preserving computations at scale to *any* blockchain. Our oracle networks are fully customizable, so each can be tailored to support general or specific computation, without requiring a hard-fork. 

> For example, an instance of an oracle network can use TEEs in conjunction with GPUs to perform machine learning tasks at scale, without compromising privacy or integrity. More details [here](https://whitepaper.portalcompute.com/technology/services/special_compute).

> Unlike privacy-preserving L1s, Portal's oracle services are blockchain-agnostic. As long as we can interface with a blockchain's smart contract, we can add private compute, democratizing access to privacy across *all* chains instead of just one L1.

