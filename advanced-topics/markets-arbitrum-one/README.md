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

For example, a 3 leverage market for the market pair BTC/USD, settled in DAI, would be referred to as:

`3-BTC/USD+DAI`

``

**Pool tokens** are named using the format:

&#x20;_`SLLLAAABBBCCCXX`_

where:

_`S` is the market's `SIDE` (L - long or S - short)_

_`LLL` is the market's`LEVERAGE` (a positive integer_ with leading zeroes_)_

_`AAA` is the `BASE` currency/token_

_`BBB` is the `QUOTE` currency/token_&#x20;

_`CCC` is the `SETTLEMENT` currency/token_

_`XX` is the market's `DEPLOYMENT CODE`_

For example, a 3p leverage Pool's _short_ token, for the market pair BTC/USD settled in DAI, would be referred to as:

`S003BTCUSDDAI00`
{% endhint %}
