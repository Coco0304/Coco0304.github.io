---
layout: post
title: Blockchain Tutorial
description: 
tag: Tutorial
---

# Blockchain

The blockchain is a ledger logging all transactions. The state of the blockchain is maintained by everyone who’s interested in the blockchain. 
![](https://github.com/siyue-zhang/images/sptdc/blk.png)

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


# P2P Network

![](https://github.com/siyue-zhang/images/sptdc/p2p.jepg)

# Decentralized Autonomous Organization

DAO is a hedge fund without manager. People put their money in DAO. DAO invests the money based on people's votes. The smart contract manages all administrative work in the company.

