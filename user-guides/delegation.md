---
description: Snapshot delegation.
---

# Delegation

## Delegation contract

Snapshot uses the Gnosis "Delegate Registry" contract here:\
[https://github.com/gnosis/delegate-registry](https://github.com/gnosis/delegate-registry)

The contract is deployed on this address: [0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446](https://etherscan.io/address/0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446#code)\
(Also available on Rinkeby and Kovan at the same address)

Delegations are stored on this subgraph:\
[https://thegraph.com/explorer/subgraph/snapshot-labs/snapshot](https://thegraph.com/explorer/subgraph/snapshot-labs/snapshot)

A delegation voting strategy must be added to the Snapshot space before delegated votes will be counted. You can use the [**with-delegation**](https://snapshot.org/#/strategy/with-delegation) strategy.

## Delegate voting power

### From Snapshot interface

1. Go to [https://snapshot.org/#/delegate](https://snapshot.org/#/delegate)
2. Enter the address you want to delegate to.
3. To limit the delegation to a specific space, tap the on switch button and enter the space key (example: `balancer.eth`) you want your delegation to take effect on. If no space is selected, the effect will take place for all spaces.
4. Click confirm to save your delegation.

### With a smart contract

You need to call the `setDelegate` method with the space id as the first argument (space id is its ENS domain name, for example _fabien.eth)_, and the address of the delegate as the second argument.

Here is an example of integration in a Solidity contract:&#x20;

[https://github.com/convex-eth/platform/blob/d3061c19b5e01a4e562c8121b08c44f1b42f0b85/contracts/contracts/BasicCvxHolder.sol#L49-L53](https://github.com/convex-eth/platform/blob/d3061c19b5e01a4e562c8121b08c44f1b42f0b85/contracts/contracts/BasicCvxHolder.sol#L49-L53)

### Supported Networks

* Mainnet
* Goerli
* Optimism
* Binance Smart Chain
* Gnosis Chain
* Matic (Polygon)
* Fantom
* Arbitrum
