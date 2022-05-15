---
description: Sorted by Category
---

# Markets (Arbitrum One)

{% content-ref url="crypto.md" %}
[crypto.md](crypto.md)
{% endcontent-ref %}

{% content-ref url="stables.md" %}
[stables.md](stables.md)
{% endcontent-ref %}

{% content-ref url="forex.md" %}
[forex.md](forex.md)
{% endcontent-ref %}

{% content-ref url="nft.md" %}
[nft.md](nft.md)
{% endcontent-ref %}

{% hint style="info" %}
**About Naming Conventions**

**Pools** are named using the format:

&#x20;_`LLL-AAA/BBB+CCC`_

where:\
_`LLL` is the market's`LEVERAGE` (a positive integer)_\
_`AAA` is the `BASE` currency/token_\
_`BBB` is the `QUOTE` currency/token_\
_`CCC` is the `SETTLEMENT` currency/token_

For example, a 3p leverage Pool for the market pair BTC/USD, settled in DAI, would be referred to as:

`3-BTC/USD+DAI`

``

**Pools tokens** are named using the format:

&#x20;_`SLLLAAABBBCCCX0`_

where:

_`S` is the market's `SIDE` (L - long or S - short)_

_`LLL` is the market's`LEVERAGE` (a positive integer_ <1000_)_

_`AAA` is the `BASE` currency/token_

_`BBB` is the `QUOTE` currency/token_&#x20;

_`CCC` is the `SETTLEMENT` currency/token_

_`X0` is the market's `DEPLOYMENT CODE`_

For example, a 3p leverage Pool's _short_ token, for the market pair BTC/USD settled in DAI, would be referred to as:

`S003BTCUSDDAIA0`

``

Confused? You can view the full rules for naming Pools and their tokens [here](../../factory/pools-factory.md). &#x20;
{% endhint %}
