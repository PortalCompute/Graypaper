---
layout: default
title: Limitations of Smart Contracts
nav_order: 1
description: ""
permalink: /technology/limitations
parent: Technology
---

# Computation
> While blockchains have revolutionized industries like finance (i.e. DeFi),  there are other industries that are currently inaccessible. One core reason is that smart contracts are unable to scale to support large computations. For example, in gaming, the existence of NFTs for in-game digital assets has drawn massive speculation; however, the implementation of the games that use them still rely on centralized servers to run. This is because moving the game logic onto a smart contract is cost-prohibitive for the reasons described below.    

## Gas
> Networks that achieve consensus (assuming an honest majority) will achieve `computational integrity`. This is why we consider blockchains like Ethereum or Bitcoin to be trustless. We can rely on a smart contract instead of a third-party because the act of achieving consensus required that the majority of nodes verified each other and computed the same output. Unfortunately, in order to achieve consensus, nodes have to artificially set an upper-limit on the amount of computation that a smart contract can perform, or else they may never reach finality. 

>On Ethereum, `gas` is the unit that measures how much effort it takes for a smart contract to perform an operation. The more complex your smart contract is, the more gas is required to execute it. In order for the network to make timely progress, the total amount of gas required by all of the contracts within a block must be limited. This upper-bound is called the `block gas-limit`. Intuitively, a larger limit implies that it will take longer to execute that block. If there were no limit at all, then a contract stuck in an infinite `while true { ... }` loop could completely freeze the network!  

> Different networks have different names for gas, but the underlying principle is the same: it is necessary for the network, but can be frustrating for the network's users and developers. The users of smart contracts take on the cost of gas which is heavily dependent on the congestion in the network. More complex Dapps may provide a richer user experience, but will require even more gas. Additionally, Dapp developers must take the gas-limit into account when developing their smart contracts, severely restricting the space of possible applications (i.e. purely to financial apps). 

## Getting around the gas-limit
> There are some computations that are so compute-intensive that it is fundamentally impossible to run on existing smart contracts without hitting the gas-limit. For example, applications like AI / Machine Learning could benefit immensely from the properties of smart contracts (i.e. transparency/immutability), but unfortunately fall under this category. So is it impossible to bring these impactful applications to the blockchains we have today?

> The only plausible solution is to move these expensive computations off-chain. Unfortunately, doing so removes us from the trustless blockchain environment where integrity is guaranteed, defeating the purpose of using the blockchain entirely. Without a means of verification, we are forced to trust that the off-chain computation was run correctly, and that computational integrity was preserved. 

> Fortunately, there are are a handful of solutions to this problem, each with their own tradeoffs: 

### Validity Proofs
> Modern cryptographic tools like Zero Knowledge Proofs (ZKPs) allow one party to prove to another that they correctly executed a program. Optionally, they do so in `zero knowledge`, leaking nothing about a secret input called the witness. The correctness of a proof can be verified in exponentially less time than the original computation would have taken. For this reason, they are extremely promising for a variety of blockchain applications. Instead of running an extremely large computation on-chain, a smart contract can verify the proof of off-chain computation for only a small gas fee. This both reduces the gas costs for users, and frees up space in blocks for more transactions, helping throughput.

> Unfortunately, ZKPs come at a cost. The overhead for generating a proof can be cost-prohibitive for larger applications. For example, ZK-ECDSA (cite) is a promising cryptographic primitive that enables anonymous voting, which is an essential tool for DAOs. Unfortunately, generating such a proof takes on the order of minutes to run, which is orders of magnitude slower than running a digital signature without a ZKP. 

> Works have been proposed to support general purpose computation within a ZKP. These primitives allow for arbitrary programs to be proven in zero knowledge, that can be verified with a short, constant-sized proof. Such constructions could supply smart contracts with arbitrary compute while preserving computational integrity. Unfortunately, such work is still in its infancy, and are far from practical. For example, TinyRam (cite) supports arbitrary programs written in a subset of C, but is only capable of executing at 10Hz. To put this in perspective, modern laptops run at around 1-3 GHz or 100-300 million times faster. 

> Attempts at hardware acceleration (i.e. FPGAs and ASICs) can help bridge this gap, but it is unlikely that they can offer more than a 100x speedup. Advances at the algorithmic level are necessary before ZKPs can be practically applied to computations that scale beyond simple transactions or financial applications.  

### Fraud Proofs
> Fraud proofs offer another means to move computation off-chain without sacrificing integrity. The idea is to optimisically trust that an operator maintained computational integrity, but to include a mechanism where a user can challenge the operator if they detect fraud. When the operator is honest, everything proceeds as normal, but at a significantly faster rate than the underlying consensus protocol. The inclusion of a challenge mechanism prevents the operator from abusing their power, and protocols that employ this technique will build in economic incentives to ensure that a rational operator will act honestly (or else face economic consequences).   

> The downside to these protocols (i.e. optimistic rollups) is that to ensure that users have sufficient time to challenge the operator, there must be a waiting period before state is finalized. In practice, this means users must wait a predetermined amount of time before they can withdraw their funds from an optimistic rollup.

### Consensus
> Just as consensus is used to guarantee that smart contracts are executed correctly on a layer-1 (i.e. everyone agrees on the next state), it can be used to guarantee the correctness of an off-chain computation. 

> For example, suppose you have a DEX with an on-chain orderbook and you want to sort all of the orders by price. This will quickly exceed the gas-limit beyond a few dozen orders. Instead, the DEX smart contract could request the sorting computation to be done off-chain. A network of nodes with a larger gas-limit can come to a quorum on the sorted orderbook and post it back to the DEX contract. Computational integrity is guaranteed as long as a threshold of the nodes were honest.

> In this scenario, it will likely be cheaper to reach consensus in the secondary network rather than the primary; however, there are some considerations. Consensus is an expensive protocol in terms of communication that doesn't scale well as the size of the network grows. Since the goal of this secondary network is to be cheaper than the primary, it is likely that the network will have to be smaller. The outcome is that secondary network will be more easily corrupted, which can undermine the security of the underlying blockchain. A larger network is necessary to secure more critical computations, but doing so will have diminishing returns in cost-reduction, defeating the purpose of offloading the computation in the first place. 

# Privacy
> The lack of privacy in smart contracts is another problem that has deterred users from participating in blockchains and has limitted use-cases for Dapps. An example of this is seen in DEXs, where orders can be front-run due to the public-by-default nature of smart contracts. Front-running is illegal in standard exchanges, but unfortunately is commonplace in DEXs, hurting retail traders. It is only possible because orders are transparent to the network. Transparency, the very property that is seen as a feature in blockchain could be problematic for certain applications.

## ZKPs
> ZKPs enable privacy since the witness input is not revealed to anyone, but there are limitations in practice. The final proof can be verified by anyone without knowledge of, or access to the secret witness. Thus in the context of blockchains where a smart contract verifies the proof, the network learns nothing of the witness. However, in the process of generating the proof, the prover required access to the witness. This is acceptable when proving something about *your* data, but breaks confidentiality when the ZKP computation is delegated elsewhere. 

> For example, ignoring the astronomical overheads involved, it is theoretically possible to prove that an AI was used correctly via ZKP. One use-case is identity services. One could prove that a that facial recognition AI outputted `match = True` when run on an input image of a face (i.e. proof-of-human for two-factor authentication). If the image is the secret witness, then a smart contract can verify the proof without revealing the image to the network. 

> This scenario is acceptable if the one generating the proof is the owner of the image. However, in practice the compute-intensive ZKP would require so much memory that only data-center server or dedicated hardware (FPGA/ASIC) would be capable of running it. Such resources are likely inaccessible to the average user, making delegation the most affordable option. Unfortunately, this reintroduces trust issues, as the delegated prover now has full custody of the image of your face.  

> In summary, ZKPs are sufficient for simple use-cases where you are proving something about your own data. As the complexity of the computation grows, the proving overhead will dictate the need for specialized provers, which compromises privacy and leads to centralization. For computations that require multiple secrets, ZKPs are insufficient, and other cryptographic primitives are necessary (i.e. MPCs). From the previous example, if the facial recognition AI were propritary, then the only acceptable prover could be the AI owner which is problematic - any other prover would require knowledge of the proprietary IP.

## Secure Multi-Party Computations (SMPCs)
> The purely cryptographic solution to the problem of trusting the prover is to use SMPCs, which are decentralized and minimize trust assumptions. Unfortunately, similar to ZKPs, the required overhead means general purpose computations will be on the order of millions to billions of times slower than the original computation would have taken, relegating MPCs to only trivial computations until algorithmic improvements are discovered.

> Specialized MPCs can yield better performance. State-of-the-art research in using MPCs for deep learning is 132x slower than non-crypto solutions (cite falcon). However, this is the difference between taking a week to train a model and two and a half years.