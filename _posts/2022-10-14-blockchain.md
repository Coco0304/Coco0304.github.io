---
layout: post
title: Blockchain Tutorial
description: 
tag: Tutorial
---

# Blockchain

![](https://github.com/siyue-zhang/images/sptdc/blk.png)


# Gas

Gas is the charge for every step of computation to prevent bad behaviors like infinite loop (denial of service attacks). When making a function call, gas fee must be paid. Each step has fixed a gas fee. Gas price of an operation is fixed but the ETH price of gas fluctuates, e.g., running at 4am when nobody is working the gas is cheap.

If a call runs out of gas, effects are discarded and **gas is not refunded**. For successful call, leftover gas is refunded. ETH has limit on block gas, if gas price is high, the smaller amount of transactions can be stored in a block. Block is full when transactions’ gas costs reach limit. Miners collect gas fees. 

# Nounce

It is the sequence number of the transaction from sender to avoid replay attacks, every transaction has an unique sequence number.

# Atomic Cross-Chain Swap