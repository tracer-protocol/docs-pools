# ❓ FAQ

#### **Where can I buy leveraged tokens?**

From [Balancer](https://arbitrum.balancer.fi/#/).

#### How long can I hold a leveraged token?

Perpetually. However, leveraged tokens suffer from volatility decay. V2's SMA pricing significantly mitigates volatility decay, but you should still monitor your tokens over long periods.&#x20;

#### **Why does it take 8 hours to mint my tokens?**

To prevent exploitation of our [new pricing](advanced-topics/mechanism/#pricing).&#x20;

#### Why has the Pools pricing changed?

To mitigate volatility decay. As v2 is more modular than v1, the original markets can still be redeployed using v2.

#### What is volatility decay?

Tokens slowly lose value over time as more get minted at low prices and burned at higher prices. When the underlying asset price is volatile, this effect is exacerbated.&#x20;

#### How does the pricing work now?

Pools use a simple moving average (SMA) of the price points from the last 8hrs. An average price smooths volatility.&#x20;

#### Where are my tokens?&#x20;

Your tokens are likely still with the Pool. You need to claim them from escrow before they appear in your wallet. If you have claimed and still can't see them, go to [troubleshooting](troubleshooting.md).&#x20;

#### Where is the liquidity mining rewards schedule?

See [Liquidity Mining](advanced-topics/liquidity-mining.md).

#### How do I get rewards?

By [staking](https://pools.tracer.finance/stakepooltoken/) leveraged tokens.&#x20;

#### Can I still use the v1 Pools?&#x20;

Yes, the pools are still operating. However, they are not shown on the application.&#x20;

## What is a Perpetual Pool?

Perpetual Pools is a derivative design using a two-sided pool to allocate collateral to long and short parties. The pool moves collateral between sides per an arbitrary transfer agreement. V1.0 contracts base the transfer agreement on a function called [power leverage](broken-reference)**.** This function determines the amount of collateral to move in a leveraged response to a changing price feed. As collateral is moved between the sides, the amount of collateral per share of the pool changes. Pool shares, then, track leveraged exposure to any price feed. These shares are tokenised, creating leveraged long and short tokens.&#x20;

## How are Perpetual Pools different from Perpetual Swaps?

Perpetual Swaps are instruments that aim to track exactly the price feed at all times, forever. The mechanism that ensures the instrument is tracking the price feed is called the funding rate. Funding rates penalise the side which has higher demand.&#x20;

In contrast, Perpetual Pools are instruments that magnify exposure to an asset based on the change in its price feed. Long and short shares (tokens) don't aim to track the price. Instead, tokens simply have power leveraged returns. The side which has higher demand pays an implicit rate to the other side in the form of [polarised gains](broken-reference).&#x20;



## Are Perpetual Pools only on Arbitrum?

For now. Arbitrum is an L2 scalability solution built on top of Ethereum. It was chosen for the initial markets because it completely inherits L1 security and greatly reduces gas costs per transaction, without compromising on decentralisation. The key benefits of Arbitrum are complete EVM compatibility and its interactive dispute resolution process which allows for no contract size limit. These benefits are currently unique to Arbitrum.

Perpetual Pools can also be deployed on the Ethereum mainnet.&#x20;

## Are there secondary markets for pool tokens?

There are Balancer AMM pools on Arbitrum for pool tokens. Traders can buy and sell leveraged tokens with these pools. As part of the [Liquidity Mining ](broken-reference)program, any trader that stakes BPT (Balancer Pool Token) for these pools will earn [TCR](broken-reference). This program aims to bootstrap secondary market liquidity.&#x20;

## How do pool Tokens differ from Binance and FTX leveraged tokens?

Binance and FTX's leveraged tokens are reliant on trusted, centralised third parties. They need a party to create the leveraged exposure for their tokens by holding a perpetual swap or lending platform position. Perpetual Pools leveraged tokens are created by a decentralised, trustless system. This system is also simple, affordable and does not have slippage or market liquidity risk.&#x20;



## What is the Rebalancing Rate? How does it affect pool token returns?

The rebalancing rate is an (inadvertent) effect of collateral skew in a pool. If there's an imbalance between long and short side collateral, the effective leverage for each side is polarised.&#x20;

A favourable rebalancing rate presents asymmetric upside for the less collateralised side. Their returns are amplified relative to their losses. For the over collateralised side, returns are minimised relative to their losses.

## Why do I have to wait until the next update to get pool tokens/collateral?&#x20;

Traders have to commit to buy pool tokens because they are created when the pool updates. The rebalancing event that happens during an update adds all the collateral that was committed during the last hour to the pool and creates the appropriate amount of tokens to return to traders. The same thing happens when a trader sells tokens to a pool. In that case, the pool destroys tokens and takes the appropriate amount of collateral from the pool to return to traders.&#x20;

## Why am I not guaranteed a token price when I mint or burn?

As stated above, pool tokens are created/destroyed during a rebalancing event. Because the rebalancing event includes the value transfer (which is calculated at the time of rebalance using the price supplied by an oracle feed), the new proportion of collateral in each side cannot be known prior to the update. Traders mint and burn tokens at the post-update rate even though they have to commit beforehand.&#x20;

## What is the front-running interval?

The front running interval is a period before an update that excludes traders' mint and burn orders from the upcoming rebalancing event. If traders don't commit before the front running interval, their orders remain queued until the following update. In Perpetual Pools V1.0, the front running interval will be 300 seconds.
