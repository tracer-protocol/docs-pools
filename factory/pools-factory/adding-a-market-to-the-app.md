# Adding a Market to the App

By default, new markets are not shown on the [pools.tracer.finance](https://pools.tracer.finance/) web application. All users can, however, use the markets by interacting with the smart contracts, third-party applications, or by importing the market to the official web application by using the "Display Alternative Pool" functionality on the [Pools](https://pools.tracer.finance/pools/) -page (_see_ [_URL parameters_](../../developer-resources/url-parameters.md)).&#x20;

## Requesting Default Inclusion to the App

Some markets are shown on the front end by default. These markets are either created by the core team and subjected to an internal validation process or have fulfilled a set of criteria and passed a DAO vote. To have your market included on the web application by default, please follow the process defined below:

1. Ensure the Market fulfils data quality criteria set by the Tracer Indices Council.
2. Ensure the Market fulfils market accuracy criteria (_see_ [_below_](adding-a-market-to-the-app.md#market-accuracy-criteria)).
3. Ensure the Market fulfils market performance criteria (see [_below_](adding-a-market-to-the-app.md#undefined)).
4. Create a proposal on [Discourse](https://discourse.tracer.finance/c/product/perpetual-pools/69) outlining the Market's purpose and providing sufficient evidence the criteria listed in 1-3 are satisfactorily fulfiled. Furthermore, the proposal should include an analysis of potential risk vectors related to using the Market, including, but not limited to, oracle performance, edge-case values, and manipulation potential. The purpose of the proposal is to probe the DAO's approval/rejection of the Market's inclusion prior to a formal voting procedure.
5. Should the Discourse sentiment be mostly positive/neutral, a Snapshot vote can be started after a period of 24 hours has passed.
6. Upon a successful governance vote, the requester can create a PR on GitHub to include the market on the front end (see [example PR](https://github.com/mycelium-ethereum/perpetual-api/pull/125)). Should the requester not have the technical ability to do this, they can alternatively reach out to the DAO's operations team on Discord.

## Market Criteria

For a new Market to be included in the [pools.tracer.finance](https://pools.tracer.finance/) web application, it has to fulfil various criteria.

### Market Accuracy Criteria

The Market needs to fulfil Market Accuracy Criteria (MAC) prior to being considered for default inclusion on the web app:

1. The Market's Name, Symbol, and Metamask Symbol should accurately reflect the Market's Parameters, Oracles, Data Manipulations, and Index Feed used.
2. The Market must not be promoted, marketed, or otherwise publicised inaccurately.

Should the Market, at any point, fail to honour an of the MACs it can be removed from the front end, subject to a governance proposal.

### Market Performance Criteria

The Market needs to fulfil Market Performance Criteria (MCP) prior to being considered for default inclusion on the web app:

1. The Market must have completed at least two Rebalances succesfully.
2. The Market must have a minimum total value locked of $10,000.00, or equivalent.
3. The Market must have a valid Keeper.
4. The Market must only reference oracles that are approved by, or fulfil the criteria set by, the Tracer Indices Council.
5. The Market's Pool Token price must be 1.000±2.5% when the initial Discourse proposal is made.

MCP 1-4 must be fulfilled at all times and the Market may be removed from the front end, subject to a governance proposal, should any of these fail. MCP 5 must be fulfilled only at the time of the initial Discourse proposal.