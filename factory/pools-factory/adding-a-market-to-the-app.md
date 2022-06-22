# Adding a Market to the App

By default, new markets are not shown on the [pools.tracer.finance](https://pools.tracer.finance/) web application. All users can, however, use the markets by interacting with the smart contracts, third-party applications, or by importing the market to the official web application by using the "Display Alternative Pool" functionality on the [Pools](https://pools.tracer.finance/pools/) -page (_see_ [_URL parameters_](../../developer-resources/url-parameters.md)).

## Requesting Default Inclusion to the App

Some markets are shown on the front end by default. These markets are either created by the core team and subjected to an internal validation process or have fulfilled a set of criteria and passed a DAO vote. To have your market included on the web application by default, please follow the process defined below:

1. Ensure the Market fulfils data quality criteria set by the Tracer Data Council.\
   _(As of June 18, 2022 these criteria have not been rolled out yet. Any verified Chainlink feed (with or without any Data Manipulations using Tracer Indices or Tracer Perpetual Pools contracts) is accepted. For a full list of Chainlink feeds, please see_ [_docs.chain.link_](https://docs.chain.link/docs/arbitrum-price-feeds/)_)_
2. Ensure the Market fulfils market accuracy criteria (_see_ [_below_](adding-a-market-to-the-app.md#market-accuracy-criteria)).
3. Ensure the Market fulfils market performance criteria (see [_below_](adding-a-market-to-the-app.md#undefined)).
4. Follow the usual governance process to include the market on the front end. Please refer to the "[How to Govern](https://dao.docs.tracer.finance/governance/governors#how-to-govern)" section in [DAO Docs](https://app.gitbook.com/o/-MbdsGfc3PEsikGQpmCo/s/c7RWzlPWCpuLBm0Xz4Xw/). In your proposal, provide sufficient evidence the criteria listed in 1-3 are satisfactorily fulfiled. Furthermore, the proposal should include an analysis of potential risk vectors related to using the Market, including, but not limited to, oracle performance, edge-case values, and manipulation potential. The purpose of the proposal is to probe the DAO's approval/rejection of the Market's inclusion prior to a formal voting procedure.
5. Upon passing the governance process successfully, the requester can create a PR on GitHub to include the market on the front end (see [example PR](https://github.com/mycelium-ethereum/perpetual-api/pull/125)). Should the requester not have the technical ability to do this, they can alternatively reach out to the DAO's operations team on Discord.
6. Make a PR to the [Pools' GitBook](https://github.com/tracer-protocol/docs-pools) repository to include the Market's information as part of the documentation. You can use the [3-BTC/USD+USDC](https://pools.docs.tracer.finance/advanced-topics/markets-arbitrum-one/crypto) information as a reference.

## Market Criteria

For a new Market to be included in the [pools.tracer.finance](https://pools.tracer.finance/) web application, it has to fulfil various criteria.

### Market Accuracy Criteria

The Market needs to fulfil Market Accuracy Criteria (MAC) prior to being considered for default inclusion on the web app:

1. The Market's Name, Symbol, Metamask Symbol, Badges, and any other data associated with the Market should accurately reflect the Market's Parameters, Oracles, Data Manipulations, and Index Feed used.
2. The Market must not be promoted, marketed, or otherwise publicised inaccurately.

Should the Market, at any point, fail to honour an of the MACs it can be removed from the front end, subject to a governance proposal.

### Market Performance Criteria

The Market needs to fulfil Market Performance Criteria (MPC) prior to being considered for default inclusion on the web app:

1. The Market must have completed at least two Rebalances successfully.
2. The Market must have a minimum total value locked of $10,000.00, or equivalent.
3. The Market must have a valid Keeper.
4. The Market must only reference oracles that are approved by, or fulfil the criteria set by, the Tracer Indices Council.
5. The Market's Pool Token price must be 1.000±2.5%.
6. The Market's Skew must be 1.000±5%.

MPC 1-4 must be fulfilled at all times and the Market may be removed from the front end, subject to a governance proposal, should any of these fail. MPC 5-6 must be fulfilled only when the governance process is initiated.
