# Arbitrum One

## Network

Perpetual Pools operate on a network called Arbitrum One. Arbitrum One is a 'layer 2' network, which means it's powered by a blockchain but, unlike the 'layer 1' blockchain, it offers lightning fast transactions and fewer fees.   &#x20;

{% hint style="info" %}
Arbitrum is a layer 2 for the **Ethereum** blockchain. It uses Ether as gas, so you'll need some in your wallet before you can start using the network. [Go back](setup.md) for help setting up.
{% endhint %}

Because it's both fast and less costly to use, Arbitrum offers a better user experience than Ethereum. To move from Ethereum to Arbitrum (and use Perpetual Pools), you'll need to send your assets to the new network. First, add it to your wallet:

### Automatically

Go to[ pools.tracer.finance](https://pools.tracer.finance/) or [bridge.arbitrum.io](https://bridge.arbitrum.io/) and connect to the site with metamask.&#x20;

### Manually

1. Open MetaMask wallet.
2. Select the network drop down.&#x20;
3. Select 'Custom RPC'.
4. Enter the following details and select 'Save'.

{% hint style="success" %}
* Network Name: **Arbitrum One**
* New RPC URL: **https://arb1.arbitrum.io/rpc**
* ChainID: **42161**
* Symbol: **AETH**
* Block Explorer URL: **https://arbiscan.io**
{% endhint %}

## Bridge&#x20;

You'll need to move your assets from ethereum to the new network to use pools. Moving from the mainnet to a layer 2 is called 'bridging'. If you don't have any assets on Arbitrum, bridge some from Ethereum or buy them directly with an on-ramp.&#x20;

## Create Custom RPC

Sometimes, the public Arbitrum RPC is slow to load. The public RPC is the one you've used to add the new network to your wallet. If you are experiencing slow loading times when you use Perpetual Pools, try setting-up a custom RPC:

1. Create an account on [Alchemy](https://www.alchemy.com/).
2. Select 'Ethereum' as the ecosystem.
3. Create an app. **Ensure you select 'Arbitrum Mainnet' as the network.**
4. Select 'VIEW DETAILS' on the application you just created.
5. Select 'VIEW KEY'.
6. Copy the HTTP link.
7. On MetaMask, switch the network to Arbitrum One (Mainnet). Note: If you have not added Arbitrum One to your wallet check out [this tutorial](https://docs.tracer.finance/tutorials/add-arbitrum-mainnet-to-metamask).&#x20;
8. Select on the 'Account' drop down and select 'Settings'.
9. Select 'Networks'.
10. Select 'Arbitrum One'.
11. Paste the copied HTTP link to replace the existing 'New RPC URL'.
12. Select 'Save'.
