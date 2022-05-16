---
description: Sorted by Category
---

# Markets (Arbitrum One)

{% hint style="success" %}
_A dynamic list of deployed Pools is available through the_ [_API_](https://api.tracer.finance/poolsv2/poolList?network=42161)_._
{% endhint %}

{% content-ref url="crypto.md" %}
[crypto.md](crypto.md)
{% endcontent-ref %}

{% content-ref url="stables.md" %}
[stables.md](stables.md)
{% endcontent-ref %}

{% content-ref url="indices.md" %}
[indices.md](indices.md)
{% endcontent-ref %}

{% content-ref url="commodities.md" %}
[commodities.md](commodities.md)
{% endcontent-ref %}

{% content-ref url="forex.md" %}
[forex.md](forex.md)
{% endcontent-ref %}

{% content-ref url="nft.md" %}
[nft.md](nft.md)
{% endcontent-ref %}

{% hint style="info" %}
**About Naming Conventions**

****

_We recommend following the naming format below when possible:_

__

**Markets** are named using the format:

&#x20;_`LLL-AAA/BBB+CCC`_

where:\
_`LLL` is the market's`LEVERAGE` (a positive integer without leading zeros)_\
_`AAA` is the `BASE` currency/token_\
_`BBB` is the `QUOTE` currency/token_\
_`CCC` is the `SETTLEMENT` currency/token_

For example, a 3 leverage market for the market pair BTC/USD, settled in USDC, would be referred to as:

`3-BTC/USD+USDC`

``

**Pool tokens** are named using the format:

&#x20;_`LLLS-AAA/BBB+CCC`_

where:

_`LLL` is the market's`LEVERAGE` (a positive integer_ without leading zeroes_)_

_`S` is the market's `SIDE` (L - long or S - short)_

_`AAA` is the `BASE` currency/token_

_`BBB` is the `QUOTE` currency/token_&#x20;

_`CCC` is the `SETTLEMENT` currency/token_

For example, a 3p leverage Pool's _short_ token, for the market pair BTC/USD settled in USDC, would be referred to as:

`S3-BTC/USD+USDC`
{% endhint %}
