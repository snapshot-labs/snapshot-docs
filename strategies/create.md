---
description: Create a strategy and use it on your own space
---

# Create a new strategy

To add your own strategy on Snapshot you need to fork the **snapshot-strategies** repository and create a pull request.

{% embed url="https://github.com/snapshot-labs/snapshot-strategies" %}

### 1. Navigate to the **`src\strategies`**

```bash
└── src
    └── strategies
        └── erc20-balance-of
```

### 2. Create a copy of the **`erc20-balance-of`** strategy folder and rename it to the name of your strategy

### 3. Write the logic of your strategy

Every strategy is, at its core, the implementation of the `strategy(space, network, provider, addresses, options, snapshot)` function.

A quick word on the function parameters:

* `space`: the space (if applicable), based on the registered ENS associated with this strategy (see [Spaces](../spaces/))
* `network`: the network id as an integer (1 for Ethereum mainnet)
* `provider`: the network provider used by the web browser
* `addresses`: the list of addresses of the voters being processed.
* `options`: a collection of options that can be passed to strategy(...) - those have no default keys and can be used to pass any useful data
* `snapshot`: the block height at which the data are queried by strategy(...) - if none is passed, 'latest' is used.

`Strategy(...)` returns a JavaScript object with every addresses from the addresses array as keys and the corresponding voting power as value (expressed in number of token owned by the address for `erc20-balance-of`, as a number of rocks owned for `has-rock`, etc).

Every strategy comes with a JSON file `examples.json`. This file is mandatory as it will be used for testing and validating the strategy before including it in Snapshot main GitHub branch. Here are the main keys:

* `"name"`: a human-reading name for the strategy ("ERC20 balance" for instance).
* `"strategy"`: the core parameters of the strategy
  * `"name"`: the strategy name ("erc20-balance-of")
  * `"params"`: optional parameters passed in `options` to strategy(...). Any useful "key":"value" can be used here and retrieved inside `strategy(...)` via `options.key`
    * `"address"`: the address of the token contract (the DAI contract for instance)
    * `"symbol"`: the token symbol ("DAI")
    * `"decimals"`: the number of decimals (18)
  * `"network"`: the network id (1 for ethereum)
  * `"addresses"`: an array of addresses which will be used for testing (they should therefore have some token)
  * `"snapshot"`: the block height (by taking a block height in the past where the addresses\[] had a positive balance, the test will be easily repeated)

Finally, all strategies will contain some similar steps, illustrated in [erc20-balance-of](https://github.com/snapshot-labs/snapshot-strategies/blob/f41f98249cff78486914473a3fef29ea960971e5/src/strategies/erc20-balance-of/index.ts):

* Getting the block height ('latest' or a specific one via the `snapshot` argument).

```
  const blockTag = typeof snapshot === 'number' ? snapshot : 'latest';
```

* Initializing Multicaller: looping over the addresses\[] array is **not allowed** as the strategy complexity would increase with the array size. Instead, Snapshot provides the Multicaller utility to group blockchain queries for a series of addresses. The abi can be in ethers human-readable form ( `['function balanceOf(address account) external view returns (uint256)']` for instance)

```
  const multi = new Multicaller(network, provider, abi, { blockTag });
```

*   Feeding data into the multicaller and executing the multicall: every query is queued in the multicaller via `Multicaller.call(...)`. Once they are all stored, an unique call is executed via `Multicall.execute()`.

    `option.address` is the token contract address (`strategy.params.address` in `examples.json`).

```
  addresses.forEach((address) =>
    multi.call(address, options.address, 'balanceOf', [address])
  );
  
  const result: Record<string, BigNumberish> = await multi.execute();
```

* Creating an object where every address from addresses\[] is paired with its corresponding value (returned from the multicall) and returning it

```
  return Object.fromEntries(
    Object.entries(result).map(([address, balance]) => [
      address,
      parseFloat(formatUnits(balance, options.decimals))
    ])
  );
```

### 4. Include your strategy in\*\*`src\strategies\index.ts` and test it with:

```javascript
npm run test --strategy=<STRATEGY NAME> // replace <STRATEGY NAME>
```

### 5. Make sure you pass the checklist

Have a look here on the requirements for adding a new strategy and make sure you full fill the points in the checklist: [https://github.com/snapshot-labs/snapshot.js/issues/212](https://github.com/snapshot-labs/snapshot.js/issues/212)

### 6. Create a pull request

The team will then review your PR and after it's approved and merged it will be available in your space settings.
