# Learn about the strategies



## How to use strategies:

If you want coin-voting (1 token = 1 vote) you can use "erc20-balance-of", however you may want:

* Delegate voting power using a delegation strategy
* Weighting voting power using a quadratic strategy
* NFT voting with an ERC-721 or ERC-1155 based strategies
* Only allow certain members to vote using whitelist strategy
* Calculate voting power from multiple chains with multichain strategy

You can combine up to 8 strategies on a single proposal (combination work as OR not AND opperator)

At the time of writing snapshot has over 150 voting strategies. Explore them here [https://snapshot.org/#/strategies](https://snapshot.org/#/strategies)\
You can even preview actions using the playground button.

## What is a strategy

A strategy is a JavaScript function that returns a score for a set of addresses. Strategies are being used on Snapshot to calculate the result for a proposal. A proposal can have multiple strategies. The default strategy is to calculate the balance of an ERC20 for each voter. A strategy can send a call to a node or subgraph.

## Example strategy

Here is an example with the most common strategy called `erc20-balance-of`.

{% embed url="https://github.com/snapshot-labs/snapshot-strategies/blob/master/src/strategies/erc20-balance-of/index.ts" %}

```javascript
import { formatUnits } from "@ethersproject/units";
import { multicall } from "../../utils";
import { abi } from "./TestToken.json";

export async function strategy(
  space,
  network,
  provider,
  addresses,
  options,
  snapshot
) {
  const blockTag = typeof snapshot === "number" ? snapshot : "latest";
  const response = await multicall(
    network,
    provider,
    abi,
    addresses.map((address: any) => [options.address, "balanceOf", [address]]),
    { blockTag }
  );
  return Object.fromEntries(
    response.map((value, i) => [
      addresses[i],
      parseFloat(formatUnits(value.toString(), options.decimals)),
    ])
  );
}
```

Strategies are defined in your space settings at `https://snapshot.page/#/<SPACE ADDRESS>/settings`. This is an example of how to add a strategy to calculate the voting power in BAL and BAL that is in Balancer pools, where they are providing liquidity.

The `erc20-balance-of` strategy setting:

```javascript
{
  "address": "0xba100000625a3754423978a60c9317c58a424e3D",
  "symbol": "BAL",
  "decimals": 18
}
```

The `balancer` strategy setting:

```javascript
{
  "address": "0xba100000625a3754423978a60c9317c58a424e3D",
  "symbol": "BAL BPT"
}
```

Strategies can be used to create a score from on-chain data, the data does not necessary need to be monetary, you can imagine a strategy that calculate how many POAP you own or use any other data available on-chain to issue a score.

### **Other Common strategies**

* **erc20-with-balance** is an example of strategy that checks whether the participant has a minimum amount of token required to vote and assigns all the votes to 1. You need to add the parameter “minBalance” and set it equal to the minimum balance required to vote on a proposal. This value is set to 0 by default.&#x20;
* **erc20-balance-of-delegate** is used if you want to use a delegation contract along with erc20-balance-of.&#x20;

### Find more strategies here: <a href="#find-more-strategies-here" id="find-more-strategies-here"></a>

{% embed url="https://github.com/snapshot-labs/snapshot-strategies/blob/master/src/strategies" %}
