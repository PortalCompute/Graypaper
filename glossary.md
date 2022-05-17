---
layout: default
title: Glossary
nav_order: 13
description: ""
permalink: /glossary
---
# Glossary
> Below is a list of commonly used technical terms in our explanations. We want our explanations to be as accessible as possible to the community.

## Artificial Intelligence (AI) terms
- **machine learning (ML)**: This is the iterative process by which a computer program is able to learn patterns in data that are not obvious to humans.
- **ML model**: Typically synonymous with **AI**, this is what is being trained or taught.
- **user data**: The input to the AI, for either training or using the AI. At Portal, we firmly believe that user data should always be in the user's custody.
- **dataset**: This is a collection of data used for training. It may contain data from one or many users. The size and quality of the data will determine the model's accuracy, and the distribution of data will affect its bias.
- **model parameters**: This sets the conditions for how the AI will learn, and what it will try to optimize for. Most often, this is simply referred to as the machine learning algorithm, or just algorithm. These parameters significantly impact the performance of an ML model.
- **training**: This is the iterative process where an AI will learn patterns from its dataset. 
- **inference**: Once an AI is sufficiently trained, it can perform useful operations. This is typically called *inference*, but other common phrases include *predictions*, *classifications*, *decisions*, or *recommendations*. For example, an AI may recommend you a song, or predict that a pedestrian will try and cross the road. 

## Blockchain-relevant terms
- **[web2](https://en.wikipedia.org/wiki/Web_2.0)**: The current popular state of the internet, which allows users to interact and collaborate with each other through social media dialogue as creators of user-generated content in a virtual community.
- **[web3](https://en.wikipedia.org/wiki/Web3)**: An idea for a new iteration of the World Wide Web based on trust-minimizing blockchain technology, which incorporates concepts such as increased decentralization, transparency, and security.


## Blockchain Properties 101
> To understand why, we must look at the properties that blockchains guarantee.
> - **consensus**: a blockchain will come to an agreement across all of its nodes about what the next block is. For blockchains like Ethereum, this means everyone has agreed on the outcomes of different computations (AKA transactions). The result is that the integrity of the computations are guaranteed (*computational integrity*), and the state cannot be arbitrarily changed without the full consent of the network (*immutability*). 
> - **transparency**: the smart contracts on a public blockchain are completely transparent to the network.
> - **censorship-resistance**: a public blockchain is accessible to anyone, democratizing access to smart contract services, regardless of where you live.

> The combination of these properties is what allows blockchains to solve trust issues. Specifically, problems in AI like opaqueness and bias can be prevented if the AI is backed by a blockchain.

## Oracles 101
> Oracles allow blockchains to connect to the real world, and typically provide smart contracts with real world data that otherwise could not be accessed (e.g. which team won the game, or what the price of a company's stock is).

> Alternatively, oracles can provide smart contracts with the results of a computation that would have been too large to run on the contract itself. This is how Portal fits into the overall picture: by providing smart contracts with the results of AI computations that are impossible to run on-chain.

### What about the blockchain properties?
> Since the oracle operates independently from the blockchains it services, the oracle must take steps to ensure that it doesn't violate the blockchains' properties. Most importantly, the oracle must guarantee that any results it sends to a smart contract have integrity. Without this, we are relegated back into the problematic world of trust.

> If there are no integrity guarantees, oracles can submit fraudulent results to influence smart contracts. For example, a dishonest oracle could report the wrong winning team to manipulate a sports-betting smart contract in their favor.

> Portal solves this by submitting unforgeable proofs alongside the AI computation's result. The succesful verification of this proof guarantees the correctness of the result. This removes the need to trust the results of a Portal oracle request.


