# Fees

> Perpetual Pools V2 contracts have 3 fee types:

## Mint Fee

The mint fee is taken from the balance of the user at entry. The funds are added to the corresponding side of the pool, i.e. long mint fees are added to the long pool and short mint fees are added to the short pool. The mint fee is determined by the creator of the pool and can be set to \[0%:100%]. The mint fee can later be adjusted by the fee controller.



## Management Fee

The management fee is taken from the aggregate balance of the pools at rebalance. The yearly management fee can be set to \[0%;10%]. The management fee is split between a primary fee receiver and a secondary fee receiver. The primary fee receiver can be set by the owner of the pool contract.

{% hint style="info" %}
Pools deployed by Tracer DAO specify the treasury as the fee recipient.
{% endhint %}



## Burn Fee

Analogous to the mint fee, the burn fee is subtracted from the total withdrawal amount of the user and redirected back to the pool the user is burning from. The burn fee is determined by the pool creator and can be set to \[0%:10%). The burn fee can later be adjusted by the fee controller.



## Default Fee Schedule

The following schedule contains the default fees. Please note that the fee structure may differ between markets. The default fees should not be constrained as a recommendation on fees. Fee amounts should be determined based on factors such as update volatility of input data, target holding period, etc.

| Leverage | Mint fee | Management fee | Burn fee |
| -------- | -------- | -------------- | -------- |
| 1        | 0.3%     | 2%             | 0%       |
| 2        | 0.6%     | 2%             | 0%       |
| 3        | 1%       | 2%             | 0%       |
| 4        | 1.5%     | 2%             | 0%       |
| 5        | 2%       | 2%             | 0%       |

{% hint style="warning" %}
_Always check the fee schedule of the pool before committing!_
{% endhint %}
