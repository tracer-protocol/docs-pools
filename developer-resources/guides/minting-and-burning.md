# Minting, Burning and Committing

Minting and burning is the primary way that users of the protocol gain access to perpetual pool leveraged tokens. For a high level explaination of minting and burning, see the [mechanism design docs](../../advanced-topics/mechanism/README.md#commits). Users of the protocol must commit to minting or burning ahead of time, with their committment executed at the pools next rebalance.

## Commit Types
There are currently six commit types supported, as defined in the [Pool committer interface](https://github.com/tracer-protocol/perpetual-pools-contracts/blob/cebd59ce0585d67e99d4db6b814bf192227e4f37/contracts/interfaces/IPoolCommitter.sol#L7).

These are
```
        ShortMint, // Mint short tokens
        ShortBurn, // Burn short tokens
        LongMint, // Mint long tokens
        LongBurn, // Burn long tokens
        LongBurnShortMint, // Burn Long tokens, then instantly mint in same upkeep
        ShortBurnLongMint // Burn Short tokens, then instantly mint in same upkeep
```
Note: You may here the `LongBurnShortMint` and `ShortBurnLongMint` commit types referenced as flip commitments.

## Committing
Minting and burning occurs by users executing a commitment via the Pool commiters [commit function](https://github.com/tracer-protocol/perpetual-pools-contracts/blob/cebd59ce0585d67e99d4db6b814bf192227e4f37/contracts/implementation/PoolCommitter.sol#L308).

Before committing, the following must occur

### Short Mint and Long Mint
- The settlement token must have been approved for spending by the LeveragedPool the user is trying to commit to.

### Short Burn and Long Burn

### Flips (Long Burn Short Mint and Short Burn Long Mint)

## Parameter Encoding
Coming Soon

## Minting
