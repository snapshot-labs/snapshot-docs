---
description: Learn how to create a new custom voting strategy.
---

# Create a voting strategy

If you can't find a strategy that fits your the needs of your space you can create a new custom one. Follow the steps below to learn how to do that:

### **1. Fork the score-api repository**&#x20;

Create a fork of the score-api repository:

{% @github-files/github-code-block url="https://github.com/snapshot-labs/score-api" %}

### **2. Duplicate the `erc20-balance-of` strategy folder**&#x20;

Navigate to `src/strategies/strategies` directory, duplicate the `erc20-balance-of` directory and rename it to the chosen name for your new strategy.

```bash
└── src
    └── strategies
        └── strategies
            └── erc20-balance-of
```

### **3. Write the logic for your strategy**

There are several files you need to edit:

#### a. `index.ts`

This file defines the logic for calculation of the voting power. As an example, the `erc20-balance-of` is taking as parameters `space`, `network`, `provider`, `addresses`, `options` and `snapshot`  in order to be able to retrieve the balances of the token specified in the `options` parameter for the provided addresses:

```typescript

import { BigNumberish } from '@ethersproject/bignumber';
import { formatUnits } from '@ethersproject/units';
import { Multicaller } from '../../utils';

export const author = 'bonustrack';
export const version = '0.1.1';

const abi = [
  'function balanceOf(address account) external view returns (uint256)'
];

export async function strategy(
  space,
  network,
  provider,
  addresses,
  options,
  snapshot
): Promise<Record<string, number>> {
  const blockTag = typeof snapshot === 'number' ? snapshot : 'latest';

  const multi = new Multicaller(network, provider, abi, { blockTag });
  addresses.forEach((address) =>
    multi.call(address, options.address, 'balanceOf', [address])
  );
  const result: Record<string, BigNumberish> = await multi.execute();

  return Object.fromEntries(
    Object.entries(result).map(([address, balance]) => [
      address,
      parseFloat(formatUnits(balance, options.decimals))
    ])
  );
}
```

#### b. `schema.json`

Describe the structure of your strategy by editing the `properties`, `required` and `additionalProperties` key-value pairs according to the logic from `index.ts` file:

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "$ref": "#/definitions/Strategy",
  "definitions": {
    "Strategy": {
      "title": "Strategy",
      "type": "object",
      "properties": {
        "symbol": {
          "type": "string",
          "title": "Symbol",
          "examples": ["e.g. UNI"],
          "maxLength": 16
        },
        "address": {
          "type": "string",
          "title": "Contract address",
          "examples": ["e.g. 0x1f9840a85d5aF5bf1D1762F925BDADdC4201F984"],
          "pattern": "^0x[a-fA-F0-9]{40}$",
          "minLength": 42,
          "maxLength": 42
        },
        "decimals": {
          "type": "number",
          "title": "Decimals",
          "examples": ["e.g. 18"]
        }
      },
      "required": ["address", "decimals"],
      "additionalProperties": false
    }
  }
}
```

#### d.  `./score-api/src/strategies/strategies/index.ts`

Import and declare you new strategy in the [`index.ts`](https://github.com/snapshot-labs/score-api/blob/master/src/strategies/strategies/index.ts) file:

```typescript
import * as yourStrategyName from './your-strategy-name';
```





#### d.  `examples.json`

Provide an example for the custom strategy setup which will be displayed on https://snapshot.org on the strategy's details page.&#x20;

Make sure to **include all the parameters you defined** above and a list of addresses to test against:

```json
[
  {
    "name": "Example query",
    "strategy": {
      "name": "erc20-balance-of",
      "params": {
        "address": "0x6b175474e89094c44da98b954eedeac495271d0f",
        "symbol": "DAI",
        "decimals": 18
      }
    },
    "network": "1",
    "addresses": [
      "0xA478c2975Ab1Ea89e8196811F51A7B7Ade33eB11",
      "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7",
      "0x1E1A51E25f2816335cA436D65e9Af7694BE232ad",
      "0x1F717Ce8ff07597ee7c408b5623dF40AaAf1787C",
      "0x1c7a9275F2BD5a260A9c31069F77d53473b8ae2e",
      "0x1d5E65a087eBc3d03a294412E46CE5D6882969f4",
      "0x1f254336E5c46639A851b9CfC165697150a6c327",
      "0x2ec3F80BeDA63Ede96BA20375032CDD3aAfb3030",
      "0x4AcBcA6BE2f8D2540bBF4CA77E45dA0A4a095Fa2",
      "0x4F3D348a6D09837Ae7961B1E0cEe2cc118cec777",
      "0x6D7f23A509E212Ba7773EC1b2505d1A134f54fbe",
      "0x07a1f6fc89223c5ebD4e4ddaE89Ac97629856A0f",
      "0x8d5F05270da470e015b67Ab5042BDbE2D2FEFB48",
      "0x8d07D225a769b7Af3A923481E1FdF49180e6A265",
      "0x8f60501dE5b9b01F9EAf1214dbE1924aA97F7fd0",
      "0x9B8e8dD9151260c21CB6D7cc59067cd8DF306D58",
      "0x17ea92D6FfbAA1c7F6B117c1E9D0c88ABdc8b84C",
      "0x38C0039247A31F3939baE65e953612125cB88268"
    ],
    "snapshot": 11437846
  }
]

```

#### e. `README.md`

Write the description of how the strategy works and provide an example of the setup. It will be displayed on the strategy's details page.

```
This is the most common strategy, it returns the balances of the voters for a specific ERC20 token.

Here is an example of parameters:

{
  "address": "0x6b175474e89094c44da98b954eedeac495271d0f",
  "symbol": "DAI",
  "decimals": 18
}
```

### **4. Test the strategy locally**

Once you saved all the files run the below command with the name of your new strategy:

```javascript
npm run test:strategy --strategy=<STRATEGY NAME> // replace <STRATEGY NAME>
```

It will trigger the tests which you can find in [this file](https://github.com/snapshot-labs/score-api/blob/master/test/strategies/unit/strategy.test.ts). If you get any errors read them carefully as they should point directly to the problem.

### **5. Review the checklist**

Ensure you meet the requirements for adding a new strategy by reviewing the checklist for adding a new strategy which can be found on [this documentation](https://github.com/snapshot-labs/score-api/blob/master/STRATEGIES.md#checklist-for-new-strategies)

### **6. Create a pull request**

Create a Pull Request with the above changes on the original [score-api](https://github.com/snapshot-labs/score-api/) repo.

The review can take the team up to 72 hours, so please be patient 🙏

After the PR has been merged, you will need to wait for the release of a new version of [Snapshot](https://snapshot.org) which can take a couple of days. Once it's deployed you can move on to the next step.

### 7. Try it out!

Head to the strategy's details page and click **Playground** button. Follow the instructions from [#testing-a-voting-strategy](../user-guides/voting-strategies.md#testing-a-voting-strategy "mention")to see if it works as you intended.

Congrats, you've just added a new custom voting strategy! :tada:
