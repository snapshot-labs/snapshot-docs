---
description: >-
  Discover the delegates of specific spaces and delegate your Voting Power
  directly through Snapshot,
---

# Delegation

## How to delegate?

Snapshot enables a couple of ways to delegate your Voting Power to another address (a delegate[^1]).

You can delegate your Voting Power via:

👉 [Delegates Registry per Space](delegation.md#delegates-registry) (if the Space has set up their custom delegation contract)

{% hint style="info" %}
This is a great solution for those who are **not sure who to delegate** their VP to.&#x20;
{% endhint %}

👉 [General Snapshot's delegation page](delegation.md#from-snapshot-interface)&#x20;

{% hint style="info" %}
The quickest solution to delegate the Voting Power to a **known address.**
{% endhint %}

👉 [Smart Contract](delegation.md#with-a-smart-contract)

{% hint style="info" %}
If you prefer to skip the interface and **interact with the Contract** directly.
{% endhint %}



Let's look at each option in detail.

### Delegates registry

It is possible to discover the delegate registry of Spaces that provided their custom delegation contract in settings.&#x20;

Head to the Space page and click **Delegates** in the left sidebar**:**

<figure><img src="../.gitbook/assets/Screenshot 2023-06-30 at 13.10.59.png" alt=""><figcaption></figcaption></figure>

You will then see a list of delegates for the Space with the number of their delegators[^2] and their total Voting Power within the Space.

<figure><img src="../.gitbook/assets/Screenshot 2023-06-30 at 13.16.55.png" alt=""><figcaption></figcaption></figure>

You can delegate your Voting Power to one of the delegates directly by clicking the **`Delegate`** button:

<figure><img src="../.gitbook/assets/Screenshot 2023-06-30 at 13.27.40.png" alt=""><figcaption></figcaption></figure>



### Delegate page

1. Go to [https://snapshot.org/#/delegate](https://snapshot.org/#/delegate)
2. Enter the address you want to delegate to.
3. To limit the delegation to a specific space, tap the on switch button and enter the space key (example: `balancer.eth`) you want your delegation to take effect on. If no space is selected, the effect will take place for all spaces.
4. Click confirm to save your delegation.

### Smart contract interaction

You need to call the `setDelegate` method with the space id as the first argument (space id is its ENS domain name, for example _fabien.eth)_, and the address of the delegate as the second argument.

Here is an example of integration in a Solidity contract:&#x20;

[https://github.com/convex-eth/platform/blob/d3061c19b5e01a4e562c8121b08c44f1b42f0b85/contracts/contracts/BasicCvxHolder.sol#L49-L53](https://github.com/convex-eth/platform/blob/d3061c19b5e01a4e562c8121b08c44f1b42f0b85/contracts/contracts/BasicCvxHolder.sol#L49-L53)

#### Supported Networks

* Mainnet
* Goerli
* Optimism
* Binance Smart Chain
* Gnosis Chain
* Matic (Polygon)
* Fantom
* Arbitrum

## Delegation contract

Snapshot uses the Gnosis "Delegate Registry" contract here:\
[https://github.com/gnosis/delegate-registry](https://github.com/gnosis/delegate-registry)

The contract is deployed on this address: [0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446](https://etherscan.io/address/0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446#code)\
(Also available on Rinkeby and Kovan at the same address)

Delegations are stored on this subgraph:\
[https://thegraph.com/explorer/subgraph/snapshot-labs/snapshot](https://thegraph.com/explorer/subgraph/snapshot-labs/snapshot)

{% hint style="info" %}
A **delegation Voting Strategy must be added** to the Snapshot space before delegated votes will be counted. You can use the [**with-delegation**](https://snapshot.org/#/strategy/with-delegation) strategy.
{% endhint %}

[^1]: By _delegate_ we mean the address which receives the delegation from another user, the _delegator._

[^2]: By _delegators_ we mean the address which has delegated their Voting Power to the _delegate_.
