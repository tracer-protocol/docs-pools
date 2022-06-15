# Upkeep & Autoclaim

## Upkeep

Keepers are Pool users that initiate the transfer and the execution of the period's commits (collectively, a **rebalance**). This function is known as Pool upkeep.

Upkeep can be performed when one period has passed since the last rebalance.

### Rebalance

Upkeep first triggers the transfer, which updates the Pools' internal long and short balances according to the transfer amount $$T$$, then the execution of burn commits, which removes funds to escrow at the updated rate, and last the execution of mint commits, which adds funds to the Pool at the updated rate (and mints tokens).&#x20;

This process is known as the rebalance.&#x20;

### Payment

Keepers are paid to perform upkeep. The payment factors for the cost of upkeep, which the keeper is reimbursed, and a tip. The tip is calculated as 5% of the cost to upkeep and increases by 5 percentage points with every block that upkeep remains eligible. The maximum keeper tip is 100%.

Payment is taken from the Pool funds. This payment is not to be confused with the [management fee](../fees.md#management).&#x20;

The keeper reward is calculated by

$$
keeperReward = (gasSpent + fixedGasOverhead )*(1+0.05+(b-1)*0.05)
$$

where&#x20;

* `fixedGasOverhead` is the amount of gas that is unreachable by gasleft() due to an error handling function and is equal to 80195.
* `gasSpent + fixedGasOverhead` is equal to the total amount of gas paid by the keeper
* `b` is the number of blocks elapsed since the pool's _updateInterval_ has passed and is capped at  20 for a maximum multiplier (brackets right of first multiplication) of 2, capping the tip at 100%.

{% hint style="info" %}
In practice, a Keeper is a bot that monitors the Pool for an opportunity to perform upkeep. Want to run a keeper? Find our implementation on [Github](https://github.com/tracer-protocol/) or talk to the team about developing your own.&#x20;
{% endhint %}

## Autoclaim

{% hint style="warning" %}
Please note that this section describes the functionality of a feature that has not been implemented yet. Currently, users need to manually claim tokens from escrow.
{% endhint %}

Autoclaim allows users to get a Pools token directly to their wallet without having to claim it separately from escrow. This is an opt-out feature on the user interface and an opt-in feature on the contract level. Users who wish to save on gas costs may choose to opt out and trade using escrow only.

Autoclaim can be performed by a keeper, known as a Claimer, immediately following a rebalance.&#x20;

### Payment

Users pay ahead of the mint and burn to have their claim automated. The payment factors for the cost of claiming, which the claimer is reimbursed, and a tip.

{% hint style="info" %}
In practice, a Claimer is a bot that monitors escrow for a profitable opportunity to perform autoclaim. Want to run a Claimer? Find our implementation on [Github](https://github.com/tracer-protocol/) or talk to the team about developing your own.&#x20;
{% endhint %}
