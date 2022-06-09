# ❓ FAQ

## UI issues

**The Pools disappear when I connect my wallet**

This is likely due to an RPC issue. In most cases we recommend changing your RPC from the default ones. If you'd like to learn how, we have a tutorial [here](https://tracer.finance/radar/remote-procedure-call-creating-an-rpc/). You can also see Offchain Labs' docs [here](https://developer.offchainlabs.com/docs/mainnet#getting-started).

## Purchasing/minting & selling/burning tokens

#### **Where can I buy leveraged tokens?**

From [Balancer](https://arbitrum.balancer.fi/#/) or directly from our [Pools -app](https://pools.tracer.finance).

#### **Why does it take 8 hours to mint my tokens?**

To prevent exploitation of our [new pricing](advanced-topics/mechanism/#pricing).&#x20;

**Are there secondary markets for Pool Tokens?**

There are Balancer AMM pools on Arbitrum for pool tokens. Traders can buy and sell leveraged tokens with these pools. As part of the [Liquidity Mining](faq.md#liquidity-mining) program, any trader that stakes BPT (Balancer Pool Token) for these pools will earn TCR. This program aims to bootstrap secondary market liquidity.&#x20;

**Why do I have to wait until the next update to get pool tokens/collateral?**

Traders have to commit to buy pool tokens because they are created when the pool updates. The rebalancing event that happens during an update adds all the collateral that was committed during the last hour to the pool and creates the appropriate amount of tokens to return to traders. The same thing happens when a trader sells tokens to a pool. In that case, the pool destroys tokens and takes the appropriate amount of collateral from the pool to return to traders.

**Why am I not guaranteed a token price when I mint or burn?**

As stated above, pool tokens are created/destroyed during a rebalancing event. Because the rebalancing event includes the value transfer (which is calculated at the time of rebalance using the price supplied by an oracle feed), the new proportion of collateral in each side cannot be known prior to the update. Traders mint and burn tokens at the post-update rate even though they have to commit beforehand.

**What is the front-running interval?**

The front running interval is a period before an update that excludes traders' mint and burn orders from the upcoming rebalancing event. If traders don't commit before the front running interval, their orders remain queued until the following update. In Perpetual Pools V1.0, the front running interval will be 300 seconds. For more information, see [Mechanism ](advanced-topics/mechanism/)under Advanced Topics.

**I still don't understand the front-running interval and the rebalance period?**

One can think about it as follows: the front-running interval is the amount of time that _has to be_ waited for, from an _economic_ perspective, to prevent front-running the price feed. From a _holistic_ perspective, you have to meet the economic constraint but also the _technical_ constraint of the update only happening at the on a period. Overall, both the _technical_ and _economic_ constraints need to be met. In the case of an 8h SMA, 1h rebalance period, means that you have to wait (at minimum) to fulfil the economic constraint (8h SMA) and, if you are unlucky, also completely wait for the technical constraint to be fulfilled, i.e. waiting another hour on top of the 8 hours.

## Holding tokens

#### How long can I hold a leveraged token?

Perpetually. However, leveraged tokens suffer from volatility decay. V2's SMA pricing significantly mitigates volatility decay, but you should still monitor your tokens over long periods.&#x20;

#### Why has the Pool Token pricing mechanism changed?

The SMA price was introduced to mitigate volatility decay. As v2 is more modular than v1, the original markets can still be redeployed using v2.

#### Where are my tokens?&#x20;

Your tokens are likely still with the Pool. You need to claim them from escrow before they appear in your wallet. If you have claimed and still can't see them, go to [troubleshooting](troubleshooting.md).&#x20;

**How do liquidations work?**

There are no liquidations in Perpetual Pools. All positions are fully funded.

## Financial concepts

#### What is volatility decay?

Tokens slowly lose value over time as more get minted at low prices and burned at higher prices. When the underlying asset price is volatile, this effect is exacerbated. You can read more about volatility decay [here ](https://tracer.finance/radar/v2-simulations)and [here](https://tracer.finance/radar/volatility-decay).

#### How does the pricing work now?

The Voyage markets introduced during the first week use a simple moving average (SMA) of the price points from the last 8hrs. An average price smooths volatility. You can read more about SMA pricing [here](https://tracer.finance/radar/v2-simulations).

**What is the Rebalancing Rate? How does it affect pool token returns?**

The rebalancing rate is an (inadvertent) effect of collateral skew in a pool. If there's an imbalance between long and short side collateral, the effective leverage for each side is polarised.&#x20;

A favourable rebalancing rate presents asymmetric upside for the less collateralised side. Their returns are amplified relative to their losses. For the over collateralised side, returns are minimised relative to their losses.

## Liquidity mining

#### Where is the liquidity mining rewards schedule?

See [Liquidity Mining](advanced-topics/liquidity-mining.md).

#### How do I get rewards?

By [staking](https://pools.tracer.finance/stakepooltoken/) leveraged tokens.&#x20;

## General

**What is a Perpetual Pool?**

Perpetual Pools is a derivative design using a two-sided pool to allocate collateral to long and short parties. The pool moves collateral between sides per an arbitrary transfer agreement. V1.0 contracts base the transfer agreement on a function called [power leverage](https://pools.old.docs.tracer.finance/perpetual-pools/mechanism-design)**.** This function determines the amount of collateral to move in a leveraged response to a changing price feed. As collateral is moved between the sides, the amount of collateral per share of the pool changes. Pool shares, then, track leveraged exposure to any price feed. These shares are tokenised, creating leveraged long and short tokens.&#x20;

**How are Perpetual Pools different from Perpetual Swaps?**

Perpetual Swaps are instruments that aim to track exactly the price feed at all times, forever. The mechanism that ensures the instrument is tracking the price feed is called the funding rate. Funding rates penalise the side which has higher demand.&#x20;

In contrast, Perpetual Pools are instruments that magnify exposure to an asset based on the change in its price feed. Long and short shares (tokens) don't aim to track the price. Instead, tokens simply have power leveraged returns. The side which has higher demand pays an implicit rate to the other side in the form of polarised gains.&#x20;

## Miscellaneous

#### Can I still use the v1 Pools?&#x20;

Yes, the pools are still operating. However, they are not shown on the Pools v2 application. Use the toggle on the top bar to switch back to v1. &#x20;

**Are Perpetual Pools available only on Arbitrum?**

For now. Arbitrum is an L2 scalability solution built on top of Ethereum. It was chosen for the initial markets because it completely inherits L1 security and greatly reduces gas costs per transaction, without compromising on decentralisation. The key benefits of Arbitrum are complete EVM compatibility and its interactive dispute resolution process which allows for no contract size limit. These benefits are currently unique to Arbitrum.

Perpetual Pools can also be deployed on the Ethereum mainnet. PPv2 is also available on Arbitrum Testnet.

**How do Pool Tokens differ from Binance and FTX leveraged tokens?**

Binance and FTX's leveraged tokens are reliant on trusted, centralised third parties. They need a party to create the leveraged exposure for their tokens by holding a perpetual swap or lending platform position. Perpetual Pools leveraged tokens are created by a decentralised, trustless system. This system is also simple, affordable and does not have slippage or market liquidity risk.&#x20;

**What happens if the Index Price goes negative?**

Perpetual Pools only accept positive prices. If the Index Price is zero or negative the Pool will pause until the Index Price returns a positive.
