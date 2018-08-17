!! Working in progress

# Plasma Plant:

A Mineable, Verifiable, and Finalizable Plasma for dApps based on Merklux, PEPoW, and the Casper FFG

## Abstract

**Plasma Plant** is an implementation of a mineable plasma chain for dApps guaranteeing its security with an accusatorial system using the **Merklux** which can verify the state transitions by managing them through a merkleized unidirectional data flow. Furthermore, we introduce **PEPoW**, Priority Exponential Proof of Work, as a partial consensus mechanism for its plasma chain which goes side by side with the Casper FFG, to maximize the benefits of the PoW without unnecessary waste of hash power.

## Introduction

Due to the fact that the Ethereum chain has a limited TPS, it is strongly required for dApps to run a separated plasma chain for their application. Thus, we have implemented a plasma chain which is mineable with the proof of stake, able to verify the state transitions on the root chain, guarantees the safe entries and exits, and finalizes plasma blocks quickly.

First, it is worth to make a plasma chain being mineable because it lets dApps not only implement their token economy but also be more decentralized by implementing the economic incentives around persistent decentralized autonomous blockchains as mentioned in the [plasma paper](https://plasma.io/). Anyone can participate in the network as a miner node with the proof of stake, and we call them "Plant." Plant proposes, validates, and finalizes the plasma blocks. Also, plant monitors and submits the finalized plasma blocks onto the root chain. As a reward, new tokens are minted and rewarded to the plants.

While we can reduce the transaction costs by submitting only the block headers of the plasma chain, we don't have a way to verify the plasma chain's state transition on the root chain. It is because the nodes on the root chain cannot access the state of the plasma chain. To resolve this problem, we use a smart contract which called Merklux, to manage the state with a merkleized unidirectional data flow. With the Merklux, we can reenact the state transitions on the root chain.

Besides, we also use an accusatorial system to guarantee safe exits from the plasma chain. A submitted plasma block includes cross-links, and they become executable when there is no accusation for the submission in a given time. Otherwise, the submitter should defend the case by verifying the state transition using the Merklux. In case of failure, related plants are slashed, and the plasma contract forfeited all of their deposits. Moreover, because of this accusatorial system, we don't need to destroy the plasma chain when a malicious submission occurred.

Basically, Plasma Plant works similar to the beacon chain, but it uses PEPoW, Priority Exponential Proof of Work, as its block proposal algorithm and finalizes the blocks with a modified Casper FFG. In Plasma Plant, for a specific epoch, every pseudo-randomly selected block proposer has own block proposing priority for each block, and the difficulty of the proof of work to produce a new block is exponential to that priority. Also, because the modified Casper FFG provides maximum rewards to the validators when they pick the highest priority blocks, the lower priority blocks may not be selected even someone produces them faster than any other block with an overwhelming hash power. As excessive hash power cannot create any value, PEPoW can be used for time-dependent jobs like substituting the `skip_count` concept of the beacon chain without unnecessary energy consumption.

To summarize, using Plasma Plant, dApp can operate an own mineable plasma chain which is verifiable on the root chain, guarantees safe exits, and finalizes its blocks quickly. Now let's deep dive into how the Plasma Plant works in more detail.

## Becoming a Plant

- Economical incentives
- Becoming a plant

## Merklux: Merkleized unidirectional data flow

proof of concept: https://github.com/commitground/merklux

- Verifiable => light weight state machine as a smart contract
-

## Accusatorial system
- Attack cases
- Long range attack

## PEPoW and the Casper FFG

proof of concept: https://github.com/commitground/PEPoW

- epoch & dynasty
- difficulty

## Governance

- proof of stake deposits
- merklux reducers

## Progress

## Contributing

## Licenses

## References




