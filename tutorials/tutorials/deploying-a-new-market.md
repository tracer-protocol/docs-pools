# Deploying a New Market: Developer Guide

One of the most exciting features of Tracer Perpetual Pools V2 is the ability for anyone, anywhere to deploy their own derivative market. The permissionless nature of Tracer means that communities and individuals have the power of derivatives at their palms.

Currently permissionless deployment is active on V2, however there is currently no interface to interact with for this, meaning you need some knowledge to be able to deploy your own market. While this interface is coming soon and will enable the everyday user to deploy new markets, there is nothing stopping you from doing this yourself, right now, with a little bit of tooling and technical know-how.

### What parameters are configurable?

Before we get into the nitty-gritty, I want to explain which parameters you can actually change.

#### Leverage

The amount of settlement tokens that are transferred from the losing side to the winning side are dependent on the change in the underlying price feed, and the **leverage**. The function for calculating this can be found [here](https://github.com/tracer-protocol/perpetual-pools-contracts/blob/5144a6e39ad3fb39ded44321bfaba64094e156c0/contracts/libraries/PoolSwapLibrary.sol#L263).

#### Update Interval

The update interval is the frequency of market updates in seconds. e.g. 3600 is 1 hour.

A market update refers to the process that occurs at a fixed time interval, where the pool’s balances are updated based on the oracle price, and new commitments are executed.\


#### Frontrunning Interval

The frontrunning interval is the minimum number of seconds one must wait before their commitment is executed. This exists because otherwise, individuals could frontrun the oracle and mint into the favourable side of a price change, capturing at least a very large percentage of the value transfer.

#### Minting & Burning Fees <a href="#minting--burning-fees" id="minting--burning-fees"></a>

The minting/burning fee is the percentage of each mint/burn that is taken and then put back into that side's collateral. This exists as a potential way to mitigate against volatility decay, because each mint adds back a little bit to the valuation of all tokens.

* It is worth noting that the burning fee should be set to a value above zero _with caution._ This is because it may be perceived as rug pull-ish if people can enter a pool, but have to pay a fee to leave. For this reason, their is a smart contract-enforced limit on the burn fee of 10%.

#### Change Interval

The changeInterval is the amount which the minting fee can change per update interval based on whether there is volatility decay. That is to say `longPrice * shortPrice < 1 -> mintingFee += changeInterval`. It is recommended to set this to 0 unless you know what you are doing.

#### The Settlement Token&#x20;

The settlement token is which ERC20 token that is used to invest into the pool. This is one of the unique features of pools. You can have an ETH/USD market settled in $gOHM. Or a BTC/ETH market settled in $WBTC. The possibilities for experimenting with new markets are endless.

* It is recommended to not use rebasing tokens for settlement.

#### Fee Controller

The address that controls the minting/burning fees and the change interval. It is recommended to set this to the Tracer developer multisig (0x0f79e82aE88E1318B8cfC8b4A205fE2F982B928A), otherwise you might have a hard time getting people to trust your market (besides, it likely won’t get approved and listed on our front-end).\


#### The Pool Name

This is just a string that can be used to identify the pool easily. It is recommended to follow the format “BASE/QUOTE+SETTLEMENT”. For example “BTC/USD+USDC” for a BTC/USD market settled in USDC. The smart contract factory automatically prepends the leverage to the pool name.

#### The Price Feed

The feed of data used to determine price changes of the leveraged tokens. For example, the `10-ETH/USD+USDC` market uses an 8 hour SMA (simple moving average) ETH/USD oracle.



#### Length of SMA Sampling Period

If you are using a SMA price feed, you can choose how many hours you want to sample from. For example, you can do the past 24 hours, or the past 5 hours, etc.

* Note that your pool’s front-running interval should generally be equal to or greater than the sample length. Your pool’s update interval should also equal the frequency of SMA polling (e.g. polling the SMA price every hour means your pool should have an update interval of 1 hour).

### How to Deploy a Pool

Now we can look at how to execute the deployment.

#### The script

There is a script in the Perpetual Pools repo that makes pool deployment easy. You can find this script here: [https://github.com/tracer-protocol/perpetual-pools-contracts/blob/73a7b787b4dca2509f010089afa3a0fea50f1cdd/scripts/deploy.ts](https://github.com/tracer-protocol/perpetual-pools-contracts/blob/73a7b787b4dca2509f010089afa3a0fea50f1cdd/scripts/deploy.ts)

Starting from [this line](https://github.com/tracer-protocol/perpetual-pools-contracts/blob/73a7b787b4dca2509f010089afa3a0fea50f1cdd/scripts/deploy.ts#L52), you can start modifying parameters. Make sure to read the comments to better understand what each one does.

#### The oracle

To make things just a little bit more complicated, you have the option of using a **spot price** oracle wrapper, or a **Simple Moving Average (SMA) price** oracle wrapper.

SMA oracle wrappers work by taking in a `ChainlinkOracleWrapper`, and wrapping itself around that. Read [these lines in the deployment script](https://github.com/tracer-protocol/perpetual-pools-contracts/blob/73a7b787b4dca2509f010089afa3a0fea50f1cdd/scripts/deploy.ts#L119-L154), to see the deployment process, and refer to the diagram below to visualise this.

\
\


![SMAOracles wrap around a ChainlinkOracleWrapper, which wraps around a Chainlink Oracle.](<../../.gitbook/assets/image (2).png>)

Because of this, you can modify the `usingSMA` variable to `false` if you would like to instead use a spot price. This will skip the deployment of the `SMAOracle`. Keeping it set to `true` will, however, deploy a spot price oracle wrapper, and deploy an `SMAOracle` using this oracle wrapper as its input price feed.

### Running the script

Once you have gone into the script and modified all of the parameters, you are ready to run the script.

First, clone the perpetual-pools contract:

```bash
git clone https://github.com/tracer-protocol/perpetual-pools-contracts.git
```

Then, set your environment variables

For Arbitrum Mainnet:

```bash
export ALCHEMY_API_ARBITRUM_URL="<YOUR_RPC_URL>"
export ARBITRUM_PRIVATE_KEY="<YOUR_PRIVATE_KEY>"
```

or for Arbitrum Rinkeby Testnet:

```bash
export ALCHEMY_API_TESTNET_URL="<YOUR_RPC_URL>"
export TESTNET_PRIVATE_KEY="<YOUR_PRIVATE_KEY>"
```

followed by

```bash
npx hardhat --network <network_name> run scripts/deploy.ts
```

where `<network_name>` is either `arb` for Arbitrum Mainnet, or `arbRinkeby`.

\


You should get output similar to this:

```bash
~/path/to/perpetual-pools-contracts$ npx hardhat --network arbRinkeby run scripts/deploy.ts 
No need to generate any newer typings.
Deployed oracleWrapper: 0xA9E26Abb9c1Bf75D2336A4dF82F5601Fec2a92dA

##### Deploying a market with the following parameters #####
poolName: BTC/USD+USDC
frontRunningInterval: 28800
updateInterval: 3600
leverageAmount: 1
settlementToken: 0xb0Ad46bD50b44cBE47E2d83143E0E415d6A842F6
oracleWrapper: 0x24De9Ffc6E1C7097bB49DC883E89CBEC519Acd18
settlementEthOracle: 0x33C0257eda38e0b85Da0ed54Bc27D03dFa62664d
feeController: 0xb0Ad46bD50b44cBE47E2d83143E0E415d6A842F6
mintingFee: 0
burningFee: 0
changeInterval: 0

Pool address: 0x2bF00aFFDFD5d95A26471CA8dcCc10e92818c281
PoolCommitter address: 0x4101704C3177533C8B442413d6874aAe70dd59e


```

{% hint style="info" %}
To view your market on the app, read the guide:  ['Displaying Custom Markets' ](https://pools.docs.tracer.finance/tutorials/tutorials/deploying-a-new-market-1)\
To get your market added to the front-end, read the guide:[ 'Adding a Market to the App'](https://pools.docs.tracer.finance/factory/pools-factory/adding-a-market-to-the-app)
{% endhint %}
