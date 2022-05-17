# Skew

The Perpetual Pools contract payoff depends on long and short demand. If the proportion of Pool funds belonging to a party is greater than 50%, the more-demanded position (pool) pays an in-kind funding rate to their counterparty (counterpool).

{% hint style="info" %}
Users that take advantage of in-kind funding are known as skew farmers. Our [User section](use-cases.md#skew-farmer) has a detailed farming guide if you'd like to implement a strategy.
{% endhint %}

This funding rate is the difference between what parties expect to receive (if the pools were equally capitalised), versus what they actually get.

## Skew

When Pool ownership is evenly split, a party takes payment, $$T$$, and their proportion of Pool funds increases by percentage $$t$$. This transaction changes the Pool ownership at an expected rate (there is no in-kind funding).&#x20;

However, when ownership is skewed, the party taking payment does not get the expected rate. Instead, they get an effective rate (less than expected if paying funding or more than expected if receiving funding).

Skew measures the split of ownership between long and short pools, and is defined as:

$$
S=l_f/s_f
$$

where $$l_f$$is the long balance and $$s_f$$is the short balance.&#x20;

## Effective Leverage

Skew can also be used to calculate a transfer's effective leverage:

$$
L_e=\begin{cases}L/S, l\\LS, s\end{cases}
$$

where $$L$$ is the Pool's leverage multiple, $$l$$ is the long party and $$s$$ is the short.

Effective leverage is what a party actually gets when they take payment. It's the real return multiple rather than the expected multiple ($$L$$). Importantly, no party pays an explicit funding rate. Rather, the Pools transfer funds regardless of the amount belonging to long and short.&#x20;

## An Analogue: The Funding Rate

While other perpetual contracts, such as perpetual swaps, often use a funding rate to inform the users of the payments made between longs and shorts, Perpetual Pools use the skew. However, when a constant of 1 is subtracted from skew, it is somewhat analogous to a funding rate;

$$
f(S)=S-1
$$

A positive rate indicates longs pay "funding" to the shorts, while a negative rate indicates the shorts pay the funding. In Perpetual Pools, the amount of "funding", however, is not directly determined by price deviations between the index and mark prices but by the imbalance between Long and Short Balances.

## Implications

While a party owns the majority of the Pool, their counterparty stands to profit more than they lose (by an amount $$|r|$$). Given the ability to hedge the Pools position, this implies that $$S\rightarrow1$$as users take advantage of the asymmetric payoff structure.&#x20;
