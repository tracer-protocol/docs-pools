# Integration Guide
Due to the permissionless nature of Tracer's contract system, integrating our Perpetual Pool derivatives is quite simple.

## Overview
There are two main ways you can integrate with Tracer's contracts.

1. You can directly interact with the contracts deplyoed on Arbitrum. This will allow you to have full control over how you interact with the system, and provides access to all Tracer functionality (minting, burning, reading data).
2. You can utilise the Tracer Pools JS SDK. This provides a much simpler way to interact with the contracts, however may not provide you all the functionality you are seeking.

It is recommended you understand the [contract mechanisms](../../advanced-topics/mechanism/README.md) as well as read the guides on [minting and burning](./minting-and-burning.md) as well as [reading pool data](./reading-pool-data.md) to understand how the Tracer contracts work for common interactions.

## Contract Resources
To begin interacting directly with the contracts, use following resources
- [Perpetual Pools Contracts](https://github.com/tracer-protocol/perpetual-pools-contracts)
- [Perpetual Pools Contract Architecture](../../advanced-topics/mechanism/README.md#implementation)
- [Mainnet and Testnet Contract addresses](../../contract-addresses.md)

## SDK Resources
To begin interacting directly with the SDK, use the following resources
- [Perpetual Pools SDK](https://github.com/tracer-protocol/pools-js)
- [Perpetual Pools Watcher](https://github.com/tracer-protocol/perpetual-pools-v2-pool-watcher)
- [Build your own Tracer bot guide](https://medium.com/tracer-dao/byob-build-your-own-bot-on-tracer-perpetual-pools-v2-a43e88e9d090)
- [Mainnet and Testnet Contract addresses](../../contract-addresses.md)