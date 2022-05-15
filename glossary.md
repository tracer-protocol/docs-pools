# 🔤 Glossary

* **Agreement**: The periodic transfer of funds between Market's parties.&#x20;
* **Address**: A 42 character alphanumeric string that identifies an Ethereum account.&#x20;
* **Annual Percentage Rate (APR)**: The rate of yearly earnings without compounding.
* **Annual Percentage Yield (APY)**: The rate of yearly compounded earnings.
* **Autoclaim**: A functionality that automatically claims Pool Tokens to the Committer's wallet. Uses a keeper to achieve autoclaim and incurs additional gas costs compared to keeping Pool Tokens in Escrow.
* **Burn**: To redeem a Pools token for the funds backing it (see _Settlement_).&#x20;
* **Burn Fee**: A fee charged to burn a Pools token _(_see _Burn)_. The fee is distributed back to the side of the Market the user is burning from. May differ between Markets but not within Markets. Not applied to V2 launch Pools.
* **Collateral**: _See "Settlement Asset"._
* **Commit**: Placing an order to enter, exit, or flip a position in a Pool.&#x20;
* **Counterpool**: the other side of the Perpetual Pool, e.g. the Short Pool is the counterpool of the Long Pool
* **Data Feed**: See _"Index Feed"_
* **Data Manipulations**: any change applied to the original oracle data before it is applied to a Perpetual Pool Market, e.g. application of a Simple Moving Average to the ETH/USD oracle feed is a Data Manipulation.
* **Deploy**: Generate a new Perpetual Pool contract instance. &#x20;
* **Deployer**: The EOA that deploys a Perpetual Pool (account _Address_).&#x20;
* **Effective Leverage**: The real multiple of the price change that a party takes as payment. It is a function of Skew and Leverage.
* **EOA**: Externally owned account.&#x20;
* **Escrow**: A database entry that tracks the ownership of Market positions that are not claimed. Saves gas using an internal record of owners rather than distributing a Pool Token. To receive the transferable Pool Token, the tokens must be claimed from Escrow.
* **Fee Receiver**: The EOAs receiving Management Fees from the market. There may be two fee receivers, a Primary Fee Receiver and a Secondary Fee Receiver, who split the fees.
* **Front Running Interval**: Time between Rebalances. Commits are processed at the end of the Front Running Interval. Trading on a Secondary Market enables instant liquidity for Pool Tokens.
* **Index Feed**: An oracle wrapper that outputs the Index Price to be used for Rebalancing. Tracer uses standardised proprietary index feeds to ensure uniformity of data.&#x20;
* **Index Price**: The current price, or value, of the tracked market, accounting for any Data Manipulations. This is the value used in calculations at Rebalance.&#x20;
* **Leverage:** A positive integer used by the Leverage Function to amplify the transfer amount relative to the price change, e.g. 3.
* **Leverage Function:** A sigmoidal function used to calculate the amount to transfer.
* **Leveraged Token**: _See "Pool Token"_.
* **Long**: Party that takes payment when the price change is positive.&#x20;
* **Long Balance**: Market's funds belonging to the long party. ****&#x20;
* **Long Pool**: The side of the Market that holds the Settlement Asset backing the Long Tokens.
* **Long Token:** A share of a Market's Long Balance, represented by an ERC-20 token.&#x20;
* **Market**: An instance of a Perpetual Pool, e.g. 3-ETH/USD+USDC. A single market is represented by a Long Token and a Short Token.&#x20;
* **Mint**: To create a new Pool Token by depositing Settlement Asset to a Market.&#x20;
* **Mint Fee**: A fee charged to mint a Pool Token (see _Mint)._ The fee is distributed back to the side of the Market the user is minting to. __ May differ between Markets but not within Markets.
* **Management Fee**: A fee charged at each Rebalance. Denoted in annualised terms. Paid to the Fee Receiver.
* **Oracle:** the EOA providing raw data. ****&#x20;
* **Perpetual Pool**: The contract that holds funds and keeps account of long and short ownership. Mints Pool Tokens when funds are added and burns Pool Tokens when funds are redeemed.
* **Pool**: See _"Perpetual Pool"._
* **Pool Token**: A transferable ERC-20 token representing ownership of either long or short funds in a Market (_also known as a_ _Leveraged Token_).&#x20;
* **Pool Owner**: The Address who owns the Market. They can set contracts to perform pool upkeep, autoclaims, and invariant checks. They can also set the Primary Fee Receiver along with the secondary fee split percentage.
* **Price Feed**: S_ee "Index Feed"_
* **Primary Fee Receiver**: The EOA receiving part of the Management Fees, 100% of the fees if a Secondary Fee Receiver is not defined.
* **Queued Trade**: A Mint or Burn that is pending processing, i.e. a trade that has been Committed but the Commit has not been executed.
* **Rebalance**: The Transfer of funds (i.e., Settlement of the Agreement) and execution of Commits.&#x20;
* **Secondary Fee Receiver**: The EOA receiving part of the Management Fees. Optionally defined and does not exist for all Markets. They can transfer the right to secondary fees to another EOA.
* **Secondary Market**: Any market (e.g., DEX, CEX, or OTC) where Long or Short Tokens can be bought & sold with the exception of the Primary Market.
* **Settlement**: When one side of a Pool makes a payment to its counterpool to settle the Agreement.&#x20;
* **Settlement Asset**: The funds used to settle a Pool Agreement. The Settlement Assets are held in the Market's Perpetual Pool contract to back shares (Pool tokens). Settlement Asset can be any non-rebasing and non-deflationary ERC-20 token, e.g. DAI or wstETH.&#x20;
* **Short**: Party that takes payment when the price change is negative.&#x20;
* **Short Balance**: Market's funds belonging to the short party.
* **Short Pool**: The side of the Market that holds the Collateral backing the Short Tokens.
* **Short Token**: A share of a Market's Short Balance, represented by an ERC-20 token.&#x20;
* **Simple Moving Average**: $$\frac{\sum P_n}{n}$$, where $$P$$ is a periodic data point and $$n$$ is the number of periods. Useful for smoothing volatility and reducing Volatility Decay.
* **Skew**: The ratio of Market funds belonging to long and short parties. Defined as `long_balance`_`/`_`short_balance`.
* **SMA**: See _"Simple Moving Average"._
* **Token**: A digital representation of ownership in ERC-20 form.
* **Total Value Locked**: Depending on the context, the total value of the funds in a Market, the Long Balance, the Short Balance, or the Tracer protocol.&#x20;
* **Tracer Indices**: Wrapper products that manipulate or standardise oracle data, e.g. SMA, and Weighted.
* **Transfer**: When funds are debited from a party and credited to their counterparty.&#x20;
* **TVL**: See _"Total Value Locked"_.
* **Pool Keeper**: Various economically incentivised actions taken by third parties to support the functioning of a Market.
* **Volatility Decay**: The loss incurred by a Short or Long Token holder due to frequent directional changes in the Index Price.
* **Wrapper**: A contract that a Pool Keeper can interface with. Transforms raw data provided by oracles.&#x20;
