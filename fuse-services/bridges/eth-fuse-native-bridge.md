---
description: >-
  Bankcoin native bridge is used to relay the Bankcoin native token between Bankcoin and
  Ethereum networks
---

# Bankcoin: Ethereum ↔ Bankcoin

Bankcoin native bridge between Ethereum and Bankcoin is used to relay the Bankcoin native token from Bankcoin to Ethereum network

## Architecture Overview

The Bankcoin bridged is based on POA's bridge implementation, it is used to transfer Bankcoin tokens between the Bankcoin chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's Bankcoin or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender. The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of Bankcoin tokens between the two networks, the bridge is also responsible for network core functionality events of relaying the block rewards to the Ethereum network:

**Mint block reward distributed on the Bankcoin chain on Ethereum**

Each cycle the total block reward distributed on Bankcoin chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on Bankcoin chain, waiting for all bridge validators on Bankcoin chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

## Contracts

Home side of the bridge on the Bankcoin network: [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://scan.bankcoin.io/address/0xd617774b9708F79187Dc7F03D3Bdce0a623F6988/transactions)

Foreign side of the bridge on the Ethereum network: [0x786Aa3227317A2e513cFE20c5897F122650bd671](https://scan.bankcoin.io/address/0x786Aa3227317A2e513cFE20c5897F122650bd671/transactions)

Bankcoin token on the Ethereum network: [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970b9bb2c0444f5e81e9d0efb84c8ccdcdcaf84d)

## Source Code

{% embed url="https://github.com/fuseio/fuse-bridge/tree/master/native-to-erc20/contracts" %}

## How to use

On Bankcoin you send native Bankcoin token to the home bridge contract. Then you receive an equal amount of the Bankcoin token on the Ethereum network, sent from the foreign bridge contract

On Ethereum network you transfer the Bankcoin token to the foreign bridge contract. After a couple of confirmations, you will receive equal amount of the Bankcoin native token, sent from the home bridge contract.

#### 

