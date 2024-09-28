---
title: Blockchain Basics
date: 2023-11-10 12:21:32
categories: web3
keywords: solidity, js
---

[From Here](https://github.com/smartcontractkit/full-blockchain-solidity-course-js)

Smart contracts are an agreement, contract or set of instructions that executes in a decentralized way without the need for a centralized or third party intermediary.

**Blockchain Oracle**: Any device that interacts with the off-chain world to provide external data or computation to smart contracts.
**Hybrid Smart Contracts**: On-Chain + Off-Chain Agreements.

Smart Contracts do trust minimized agreements that cannot be broke.

- Cannot be altered (immutable)
- Automatically executes
- Everyone sees the terms of agreement

UNBREAKABLE AGREEMENTS
and much more.

1. Decentralized
2. Transparency
3. Speed
4. Security
5. Remove counterpart risk
6. True trust minimized agreements

DeFi → Decentralized Finances
DAO → Decentralized Autonomous Organizations
NFT → Not Fungible Token

### Your First Transaction

1. Set up a wallet with [Metamask](https://metamask.io)
2. We can see details with the [Etherscan](https://etherscan.io)
- Mnemonic → can access all of your accounts.
- Private Key → can access 1 of your accounts.
- Public Key → can access nothing.
3. Connect and get ETH for test in [Faucets](https://faucets.chain.link)

### Gas I: Introduction to Gas

When we make transactions, the miners or validators make a small fee related to the gas.
**Gas**: A unit of computational measurement. The more complex your transaction is the more gas you have to pay.

Transaction Fee = Gas Price * How much Gas used.

### How Blockchain Works

**Block**: A block of data encrypted in some hash (e. g. Sha256) with code (named nonce) to validate the block and hash validated that must start with 4 zeros.
**Blockchain**: Each block has an prev hash that refer to previous block in the chain.
Genesis Block: The first block in a blockchain.

When a block is edited, broke all the next blocks. Then all the blocks need to be mine again.
After mine all this blocks, this blockchain is different from all the others in the decentralized net so it is discarted.

**Mining**: The process of finding the solution to the blockchain problem.
In our example, the problem was to find a hash that starts with four zeros.
Nodes get paid for mining blocks.

**Private Key**: Key used to sign an transaction.
**Public Key**: Key used to validate an signed transaction.

### Gas II: Block Rewards & EIP 1550

**Base Fee**: Minimum gas price to send your transaction.

**EIP (Etherium Improvement Proposals)**: The comon way of requesting changes to etherium network.

### High-level blockchain fundamentals.

**Node**: A single instance in a decentralized network.

Anybody can run an Etherium node easily.
Blockchain nodes keep lists the transactions that ocur.

**Consensus** is the mechanism used to agree on the state of a blockchain. And it can be broke in two parts:
1. Chain Selection Algorithm: using Nakamoto Consensus, the longest chain is selected.
2. Sybil Resistance Mechanism: is a blockchain ability to defend against users creating a large number of pseudo anonymous identities to gain a disproportionately advantageous influence over the set system.
  - Proof of Work: the problem that need to be solved. It can be more hard and expensive depending to block time need to be. The gas fee is paid to the miner that resolve the transaction.
  - Proof of Stake: it randomly choose and validator in the network. the gas fee is paid for validator, not miners.

**Block Confirmations**: the number of confirmations is the number of blocks added on after our transaction.

Sharding: sharded blockchain is an blockchain of blockchains. Is a main chain that is going to coordinate everything. Can be an solutions to scalability problem when an chain has to much transactions.
Layer 1: Base layer implementation.
Layer 2: Any application build on top of a layer 1.
Roll Ups: chains in the layer 2 that send (roll up) their transactions to layer 1.

Attacks:
- **Sybil Attack**: when a user creates a whole bunch of pseudo anonymous account to try to influence the network.
- **51% Attack**: when a user, or a group of users, creates an chain that is longer of all others.

### Welcome to Remix! Simple Storage

Solidity is the primary smart contract coding language.

Contract is an keyword to define the start of an contract in code.

Coding an contract:
1. Goto [Remix Etherium IDE](remix.etherium.org)
2. Init an project with an Solidity (`.sol`) file.
3. Set solidity version. Ex.:
  - `pragma solidity 0.8.7;` to set 0.8.7 version.
  - `pragma solidity ^0.8.7;` to set an version above 0.8.7.
  - `pragma solidity >=0.8.7 < 0.9.0;` to set an version between 0.8.7 and 0.9.
4. Put spdx licence on top of code.
5. Define an contract with the keyword `contract` in the code. Contract in solidity is similar with
Classes like in any other object-oriented languages. Ex.:
  - `contract SimpleStorage {}`. create an contract named SimpleStorage with no one content.

Solidity Types:

The concept of “undefined” or “null” values does not exist in Solidity, but newly declared 
variables always have a default value dependent on its type.

> Any time you change something on-chain, including making a new contract, it happens in a 
> transaction.


