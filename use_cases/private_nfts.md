---
layout: default
title: Private NFTs 
nav_order: 6
description: ""
permalink: /use_cases/private_nfts
parent: Use Cases
---


# Private NFTs
> A vast majority of NFTs are public by nature. Transparency presents a multitude of limitations to NFTs on leading blockchains. As an oracle service, Portal Compute can extend the current capabilities of L1 chains to handle private NFTs. To understand the use cases of private NFTs, consider the following limitations:
1. The content of NFTs, represented by the metadata, is public.
2. All interactions with NFTs are public, including viewing a token’s ownership and ownership history.
3. There is no ability to issue access control to NFTs.

>Solutions that currently exist require the adoption of a whole new Layer-1 to mint, share, and interact with private NFTs. Our solution offers the ability for a user to mint a private NFT right on the Ethereum blockchain, or any other blockchain, natively. Users will be able to mint an NFT using our generalized Portal NFT smart contract, then have that NFT metadata viewable only by addresses specified by the owner of the NFT. These permissions can also follow rules based on certain conditions for that address. 

> For example, a content creator can make media like a movie visible for only a 7-day rental. When an address seeks to view the metadata, ownership, or history of the NFT, they submit a `read` request to a Portal `NFT OIC` on their chain. The *PCON* will verify that the reader's address is whitelisted by the content creator / NFT owner to view the NFT. The metadata can then be encrypted such that only the reader can decrypt it. 

> These interactions will be expanded on in the future and can unlock new use cases for metaverse games, private art galleries, musicians, and any media creator who wants an alternative to monetizing that is better than the current solely public nature of NFTs on the blockchain.
