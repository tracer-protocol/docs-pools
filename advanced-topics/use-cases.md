# Use cases

## Speculation

You can use the Perpetual Pools contract to express a belief that the performance of the index feed is either positive (long tokens) or negative (short tokens). As the Perpetual Pools markets can be settled in various assets, you can hold high-conviction assets while taking a view on other markets as well. Hence, you do not need to give up your exposure to the settlement asset.

## Hedging

You can use Perpetual Pools to offset your exposure to the price movement in the underlying asset. This protection of the downside risk comes at the cost of potential upside.

> For example, a user holds three ether and wants to hedge the entire position. They can do so by entering a short position with an amount equivalent to one ether in a 3-ETH/USD Pool. The profits of one position offset the losses of the other. &#x20;

## Skew Farming

You can enter a Pool position to take advantage of in-kind funding payments. By doing so, you exploit the difference between[ effective leverage](mechanism/skew.md#effective-leverage) and expected leverage to make risk-adjusted returns.&#x20;

{% hint style="info" %}
Like the sound of excess risk-adjusted returns? We do too. Here's our guide for skew farming with the V2 contracts: [here](https://tracer.finance/radar/skew-farming-explained)
{% endhint %}

## Liquidity Provision (LP)

You can provide secondary market liquidity by taking a Pools position and making it available by LPing on a secondary market. By supplying the secondary market with Pools tokens and other assets in a pre-determined proportion, you can capture trading fees and any rewards offered by the market for adding liquidity.&#x20;

Here's how to provide liquidity for our known secondary markets:&#x20;

#### Balancer

{% tabs %}
{% tab title="ETH" %}
**Step 1:**

Mint both long and short tokens in equal amounts for any of the following Pools:

1. 3-ETH/USD+USDC

{% hint style="info" %}
Not sure how to mint? Check out the [Quick Start](../quick-start-guide/4.-minting-and-burning.md). &#x20;
{% endhint %}

**Step 2:**

Head over to [Balancer](https://arbitrum.balancer.fi/#/) and find your Pool's corresponding investment strategy&#x20;
{% endtab %}

{% tab title="BTC" %}
**Step 1:**

Mint both long and short tokens in equal amounts for any of the following Pools:

1. 3-BTC/USD+USDC

{% hint style="info" %}
Not sure how to mint? Check out the [Quick Start](../quick-start-guide/4.-minting-and-burning.md). &#x20;
{% endhint %}

**Step 2:**

Head over to [Balancer](https://arbitrum.balancer.fi/#/) and find your Pool's corresponding investment strategy&#x20;
{% endtab %}

{% tab title="Miscellaneous" %}
The process will be the same for any other tokens!
{% endtab %}
{% endtabs %}
