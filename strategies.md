# Strategies

A strategy is a JavaScript function that return a score for a set of addresses. Strategies are being used on Snapshot to calculate the result for a proposal. A proposal can have multiple strategies, the default strategy is to calculate the balance of an ERC20 for each voters. A strategy can send call to a node or subgraph.

This is the strategy `erc20-balance-of`:

{% embed url="https://github.com/bonustrack/snapshot.js/blob/master/src/strategies/erc20-balance-of/index.ts" %}

```javascript
import { formatUnits } from '@ethersproject/units';
import { multicall } from '../../utils';
import { abi } from './TestToken.json';

export async function strategy(provider, addresses, options, snapshot) {
  const blockTag = typeof snapshot === 'number' ? snapshot : 'latest';
  const response = await multicall(
    provider,
    abi,
    addresses.map((address: any) => [options.address, 'balanceOf', [address]]),
    { blockTag }
  );
  return Object.fromEntries(
    response.map((value, i) => [
      addresses[i],
      parseFloat(formatUnits(value.toString(), options.decimals))
    ])
  );
}
```

Strategies are defined in the space `index.json` file level. This is how to add strategies to calculate the balance of voters in BAL and balance of BAL in Balancer pools where they provide liquidity. 

{% embed url="https://github.com/bonustrack/snapshot-spaces/blob/master/spaces/balancer/index.json\#L20-L30" %}

```javascript
{
  ...
  "strategies": [
    ["erc20BalanceOf", {
      "address": "0xba100000625a3754423978a60c9317c58a424e3D",
      "symbol": "BAL",
      "decimals": 18
    }],
    ["balancer", {
      "address": "0xba100000625a3754423978a60c9317c58a424e3D",
      "symbol": "BAL BPT"
    }]
  ]
}
```

Strategies can be used to create a score from on-chain data, the data does not necessary need to be monetary, we can imagine a strategy that calculate how many POAP you own or use any other data available on-chain so issue a score.

