# Pools Factory

{% hint style="danger" %}
Please note this page refers to an upcoming extension to Tracer Perpetual Pools and the features presented here may not yet be available!
{% endhint %}

Welcome to the Pools Factory guide. Here, we'll show you how to customise your own Perpetual Pool and deploy it on Arbitrum using Tracer's Factory app. If you are looking for additional ways to edit and deploy the contracts, our [Development Guide](../developer-resources/development-guide/) has you covered.&#x20;

{% hint style="warning" %}
You must use a standardised Tracer Index Feed as the input to a Perpetual Pool contract. You can use the Index Feed Factory to standardise existing data feeds.
{% endhint %}

## Creating a New Market

{% hint style="danger" %}
This part of the documentation is still incomplete. Please note that any details provided here may be inaccurate or unrepresentative of the functionality of the Factory or Perpetual Pools.
{% endhint %}

The easiest way to create a new Perpetual Pool Market is by using the Tracer Factory. You will need to define the following inputs to a market:

* Pool Name (`string`)
* Front Running Interval (`uint`) (seconds) (the minimum number of seconds that must elapse before a commit can be executed; range \[0;2^32]; must be smaller than the Update Interval)
* Update Interval (`uint`) (seconds) (the minimum number of seconds that must elapse before a price change; defaults to 300; range \[0;2^32] seconds; must be greater than the Front Running Interval)
* Leverage Amount (`uint`) (the amount by which price movements are amplified; must be a positive integer)
* Settlement Token (`address`) (address of the token in which the Market is settled; must be ERC-20, non-rebasing and non-deflationary)
* Oracle Wrapper (`address`) (pricing data used for Rebalance; must be a standardised Tracer Index Feed)
* Settlement Eth Oracle (`address`) (the oracle to fetch the price of Ether in terms of the Settlement Token; must be a standardised Tracer Index Feed)
* Minting Fee (`uint`) (the fee charged for mints, given as `percentage / 100 * 10^18`; range \[0%;100%))
* Burning Fee (`uint`) (the fee charged for burns, given as `percentage / 100 * 10^18`; range \[0%;10%))

The parameters that you cannot change are:

* Fee Controller (`address`) (this address has control over fee parameters)

The market will be deployed to a deterministically defined address. The market's details will include the following:

* Pool Committer Address (`address`) (address of new Pool Committer)
* Pool (`address`) (address of the pool associated with the Pool Committer)
* Invariant Check (`address`) (address of the invariant check)

## Interacting with a Deployed Market

You can interact with the market with the following functions:

