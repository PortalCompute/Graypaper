---
layout: default
title: DeFi 
nav_order: 6
description: ""
permalink: /use_cases/defi
parent: Use Cases
---


# Private NFTs
> A vast majority of NFTs are public by nature. This presents a multitude of limitations to the current NFT economy on major chains. As an oracle service, Portal Compute can extend the current capabilities of Layer-1 chains to be handle private NFTs. To understand the use cases of private NFTs, consider the following current limitations of NFTs:
1. The content of the NFT, represented by the metadata, are public.
2. All interactions with the token are public, including viewing ownership and ownership history.
3. There is no ability to issue access control

>Solutions that currently exist require the adoption of a whole new Layer-1 to mint, share, and interact with private NFTs. Our solution offers the ability for a user to mint a private NFT right on the Ethereum blockchain natively. Users will be able to mint an NFT using our generalized Portal NFT smart contract, then have that NFT metadata viewable only by addresses specified by the owner of the NFT. These permissions can also be based on certain conditions for that address. For example, a content creator can make media like a movie visible for only a 7-day rental. When an addresss seeks to view the metadata, ownership, or history of the NFT, they'll submit a `read` request to our Portal NFT smart contract on their chain, which will be read along with the requester's address, along with the private NFT they're trying to access. The contract will verify that the reader's address is whitelisted by the content creator to view the NFT. These interactions will be expanded on in the future, and can unlock new usecases for metaverse games, private art galleries, musicians, and any media creator who wants an alternative to monetizing that is better than the current solely public nature of NFTs on the blockchain.