---
layout: post
title: Blockchain Jargons
description: 
tag: Tutorial
---

# Blockchain

The blockchain is a ledger logging all transactions. The state of the blockchain is maintained by everyone who’s interested in the blockchain. 
![](http://siyue-zhang.github.io/images/sptdc/blk.png)

# Escrow

Escrow means to let the contract owns the asset during the transaction. If the transaction is complete, the asset is traded. Otherwise, the asset is refunded to the original owner. Escrow must be temporary, otherwise the lock can be forever if the counterparty walks off.

# Gas

Gas is the charge for every step of computation to prevent bad behaviors like infinite loop (denial of service attacks). When making a function call, gas fee must be paid. Each step has fixed a gas fee. Gas price of an operation is fixed but the ETH price of gas fluctuates, e.g., running at 4am when nobody is working the gas is cheap.

If a call runs out of gas, effects are discarded and gas is not refunded. For successful call, leftover gas is refunded. ETH has limit on block gas, if gas price is high, the smaller amount of transactions can be stored in a block. Block is full when transactions’ gas costs reach limit. Miners collect gas fees.

# GasToken

ETH gives a gas refund for releasing unneeded storage by overwriting with 0s. This incentive can be exploited by allocating the memory and paying fees when gas is cheap, then freeing the memory when gas is expensive and getting refund. Thus, the memory is purely allocated for speculation.

# Nounce

It is the sequence number of the transaction from the sender to avoid replay attacks, every transaction has an unique sequence number.

# Atomic Cross-Chain Swap

An atomic swap is an exchange of cryptocurrencies from separate blockchains. The term atomic derives from the term "atomic state" in which a state has no substates: the transaction either happens or doesn't. Atomic swaps use Hash Timelock Contracts (HTLC) to automate the exchange of tokens. As its name denotes, HTLC is a time-bound smart contract between parties that involves generating one cryptographic hash on each end.

# P2P Network

![](http://siyue-zhang.github.io/images/sptdc/p2p.jpeg)

# Decentralized Autonomous Organization

DAO is a hedge fund without manager. People put their money in DAO. DAO invests the money based on people's votes. The smart contract manages all administrative work in the company.

# State Machine

A machine that maintains some given program state and future states allowed on that machine. Blockchains are state machines that are instantiated with some genesis state and have very strict rules (i.e., consensus) that define how that state can transition.

# Web 3.0

Web2 refers to the version of the internet that dominated by companies that provide services in exchange for personal data. Web3, in the context of Ethereum, refers to decentralized apps that run on the blockchain.

Web3 Benefits:

* Anyone who is on the network has permission to use the service – or in other words, permission isn't required.
* No one can block you or deny you access to the service.
* Payments are built in via the native token, ether (ETH).
* Ethereum is turing-complete, meaning you can program pretty much anything.

In Web 3.0 you can write smart contracts that define the logic of your applications and deploy them onto the decentralized state machine. This means that every person who wants to build a blockchain application deploys their code on this shared state machine.

![](http://siyue-zhang.github.io/images/sptdc/web3arc.png)

# Ethereum Virtual Machine (EVM)

EVM executes the logic defined in the smart contracts and processes the state changes that happen on this globally accessible state machine. The EVM doesn’t understand high-level languages like Solidity and Vyper, which are used to write smart contracts. Instead, you have to compile the high-level language down into bytecode, which the EVM can then execute.

# Decentralized Off-Chain Storage

## IPFS

[https://ipfs.io](https://ipfs.io/)

The IPFS system distributes and stores the data in a peer-to-peer network. IPFS also has an incentive layer known as “Filecoin.” This layer incentivizes nodes around the world to store and retrieve this data. 


## Swarm

[https://www.ethswarm.org](https://www.ethswarm.org/)

While Filecoin is a separate system, Swarm’s incentive system is built-in and enforced through smart contracts on the Ethereum blockchain for storing and retrieving data.


# Polkadot

The blockchain of blockchains. 

# L2 Scaling Solutions

Instead of executing transactions on the main blockchain, **sidechains** process and execute transactions. Every so often, the sidechain submits an aggregation of its recent blocks back to the primary chain.

Other examples of L2 solutions are **Optimistic Rollups** and **ZK-Rollups**. The idea here is similar: We batch transactions off-chain using a “rollup” smart contract and then periodically commit these transactions to the main chain.

# Network Effect

The network effect is a phenomenon whereby increased numbers of people or participants improve the value of a good or service. 

> “Token networks align network participants to work together toward a common goal — the growth of the network and the appreciation of the token.” — Chris Dixon

# Payment Channels: bar tabs for blockchains

**Open/Deposit**: Pick a party you want to make payments with
* Escrow funds on the blockchain under both your control
* Get IOU for those funds

**Transact**: Make payments to and from conterparty by changing the balance on the IOU

**Close**: Use IOU to retrieve money from blockchain

Identities are costly in payment channels because nodes need to escrow money as deposit. Identities are long lived.

Payment channel network can be formed by multiple bilateral channels.