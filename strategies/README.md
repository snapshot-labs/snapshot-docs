# Strategies

A strategy is a JavaScript function that returns a score for a set of addresses. Strategies are being used on Snapshot to calculate the result for a proposal. A proposal can have multiple strategies. The default strategy is to calculate the balance of an ERC20 for each voter. A strategy can send a call to a node or subgraph.

## This is the default strategy used `erc20-balance-of`

{% embed url="https://github.com/bonustrack/snapshot.js/blob/master/src/strategies/erc20-balance-of/index.ts" caption="" %}

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

Strategies are defined in your space settings at `https://snapshot.page/#/<SPACE ADDRESS>/settings`. This is an example how to add a strategy to calculate the voting power in BAL and BAL that is in Balancer pools, where they are providing liquidity.

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

### More strategies here:

{% embed url="https://github.com/bonustrack/snapshot.js/tree/master/src/strategies" caption="" %}

