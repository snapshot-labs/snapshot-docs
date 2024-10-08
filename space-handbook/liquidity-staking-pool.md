---
description: >-
  Include tokens added in liquidity pools or staking contracts into Voting Power
  calculation besides those held in users' wallets.
---

# Liquidity / staking pool

At the moment, Snapshot already supports calculating the Voting Power of the underlying token in the LP/staking contract from the most popular AMMs[^1] like Uniswap v2 and v3, Balancer, or SushiSwap.

This page only goes through popular strategies as projects may have a different method to call deposited balance in their contracts, which is often customized for a specific use case.

By enabling such a strategy in your space, you can allow the proposal to capture more users interested in your governance.&#x20;

Some spaces allow only users holding tokens in liquidity/staking pools to have Voting Power.

### [uniswap](https://snapshot.org/#/strategy/uniswap)

The strategy fetches the balance of the input token address in all **Uniswap-v2** liquidity pools.

This allows uni-v2 LP token holders to vote based on the underlying token cumulated in each pool.

{% hint style="info" %}
For instance, users who have 1 DAI in the DAI-USDC pool, and 2 DAI in the DAI-ETH pool, will have **3 Voting Power**.
{% endhint %}

**Strategy setup:**

```
{
  "address": "0x6b175474e89094c44da98b954eedeac495271d0f",
  "symbol": "DAI"
}
```



You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/uniswap?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4NmIxNzU0NzRlODkwOTRjNDRkYTk4Yjk1NGVlZGVhYzQ5NTI3MWQwZiIsInN5bWJvbCI6IkRBSSJ9LCJuZXR3b3JrIjoiMSIsInNuYXBzaG90IjoiIiwiYWRkcmVzc2VzIjpbIjB4NzkzMTdmYzBmYjE3YmMwY2UyMTNhMmI1MGYzNDNlNGQ0YzI3NzcwNCJdfQ.." %}

### [staked-uniswap](https://snapshot.org/#/strategy/staked-uniswap)

Many platforms offer decent yields on one's Uniswap LP tokens.&#x20;

By staking in their farms, users transfer their LP tokens to the contract they are interacting with (staking contract) and then can earn rewards from the farm they have joined.&#x20;

The specific type of LP that can be farmed depends on the individual platforms.

The `staked-uniswap` strategy allows you to get token balance of an LP in a staking contract.

**Strategy setup:**

* `tokenAddress`: the underlying token you want to use to calculate Voting Power
* `uniswapAddress`: the Uniswap LP address where users can deposit their token
* `stakingAddress`: the staking contract address where users stake their LP token

```
{
  "tokenAddress": "0x6e36556b3ee5aa28def2a8ec3dae30ec2b208739",
  "uniswapAddress": "0xdf6b861b4fbcfaffb62dd1906fcd3a863955704b",
  "stakingAddress": "0xfd15657341492d1918e3a8b7421e9627d52056e9",
  "symbol": "BUILD",
  "decimals": 18
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/staked-uniswap?query=eyJwYXJhbXMiOnsidG9rZW5BZGRyZXNzIjoiMHg2ZTM2NTU2YjNlZTVhYTI4ZGVmMmE4ZWMzZGFlMzBlYzJiMjA4NzM5IiwidW5pc3dhcEFkZHJlc3MiOiIweGRmNmI4NjFiNGZiY2ZhZmZiNjJkZDE5MDZmY2QzYTg2Mzk1NTcwNGIiLCJzdGFraW5nQWRkcmVzcyI6IjB4ZmQxNTY1NzM0MTQ5MmQxOTE4ZTNhOGI3NDIxZTk2MjdkNTIwNTZlOSIsInN5bWJvbCI6IkJVSUxEIiwiZGVjaW1hbHMiOjE4fSwibmV0d29yayI6IjEiLCJzbmFwc2hvdCI6IiIsImFkZHJlc3NlcyI6WyIweDg3NjE2ZkE4NTBjODdhNzhmMzA3ODc4ZjMyRDgwOGRhZDhmNGQ0MDEiXX0." %}

### [uniswap-v3](https://snapshot.org/#/strategy/uniswap-v3)

In comparison with [v2](liquidity-staking-pool.md#uniswap), **Uniswap v3** provides users with the most flexibility and granular control over personal assets by introducing features like concentrated liquidity and multiple LP fee tiers per pair — 0.05%, 0.30%, and 1.00%.

In this context, the USDC / ETH LPs with 0.3% and 0.05% fees represent different contract addresses (`poolAddress)` respectively.

The demo illustrates how to get **USDC** balance in the **USDC / ETH** 0.3% liquidity pool. If you want to calculate the other token in the pool, you can change the param`tokenReserve` to 1.

**Strategy setup:**

```
{
  "symbol": "USDC",
  "poolAddress": "0x8ad599c3A0ff1De082011EFDDc58f1908eb6e6D8",
  "tokenReserve": 0
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/uniswap-v3?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiVU5JIiwicG9vbEFkZHJlc3MiOiIweGZjOWY1NzIxMjRkOGY0Njk5NjBiOTQ1MzdiNDkzZjI2NzY3NzZjMDMiLCJ0b2tlblJlc2VydmUiOjB9LCJuZXR3b3JrIjoiMSIsInNuYXBzaG90IjoiIiwiYWRkcmVzc2VzIjpbIjB4MWE2MmM5ZDE3NDZkZTlmZDlkNDQ5ZTgwZGRiYjhhNjdkMmE3MmE5NCIsIjB4NzkwMzk4NzI2YTY4YTJlODFhZWMzZWQwZjdjYzM3NThiY2NjNTY4MSJdfQ.." %}

### [sushiswap](https://snapshot.org/#/strategy/sushiswap)

LP tokens provided in **SushiSwap** are called **SLP** tokens, and the SLP tokens can be staked into the farm (MasterChef LP Staking Pool) to earn rewards.

This strategy can return the balance of the underlying token in SushiSwap's **LP pools and farms** as well.

**Strategy setup:**

* `address` - the underlying token address
* `useStakedBalances` - if **true** it will also return the token balances from the MasterChef LP Staking Pool
* `masterchefVersion` - if **v2** it will return the token balances from the MasterChef V2 staking contract instead of MasterChef V1.

```
{
  "address": "0x0Ae055097C6d159879521C384F1D2123D1f195e6",
  "useStakedBalances": "true",
  "masterchefVersion": "v1"
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/sushiswap?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4Y2FmZTAwMTA2N2NkZWYyNjZhZmI3ZWI1YTI4NmRjZmQyNzdmM2RlNSIsInN5bWJvbCI6IlBTUCIsInVzZVN0YWtlZEJhbGFuY2VzIjoidHJ1ZSIsIm1hc3RlcmNoZWZWZXJzaW9uIjoidjIifSwibmV0d29yayI6IjEiLCJzbmFwc2hvdCI6IiIsImFkZHJlc3NlcyI6WyIweDA1ODQ3NmVkYWNiMjNlOTUwN2NmZjM3OWU3ZGQ4Y2Y0ZGVlNGQyZGIiLCIweDViYTQ3ZjhjNjRmY2Y1NWU5ODZlMmYzNzg2MGI5MWI1MDFkMWIxZWQiXX0." %}

### [masterchef-pool-balance](https://snapshot.org/#/strategy/masterchef-pool-balance)

The MasterChef contract has been developed by many projects based on SushiSwap’s original contract like [pancake's syrup pool](https://docs.pancakeswap.finance/products/syrup-pool). With MasterChef, **users can stake their tokens and in exchange they will get a token reward.**&#x20;

The strategy is more generic and it gets the balance of the LP token or the underlying base token in the LP from a MasterChef staking pool.&#x20;

**Strategy setup:**

* `chefAddress`: Masterchef contract address
* `pid`: masterchef pool id (starting with zero)
* `uniPairAddress`: address of a Uniswap pair (or a sushi pair or any other with the same interface)
  * if `uniPairAddress` is null, returns staked **LP token balance** as is
  * if the `uniPairAddress` option is provided, converts staked LP token balance to **base token** balance (based on the pair total supply and base token reserve)
* `tokenIndex`: index of a token in LP pair, by default 0, can switch to 1 for another base token
* `weight`: integer multiplier of the result (for combining strategies with different weights | **optional**)
* `weightDecimals`:  integer divisor of the result (1 gives a decimal before the result | **optional**)

```
{
  "symbol": "CHEF",
  "chefAddress": "0xD38abbAeC03a9FF287eFc9a5F0d0580E07335D1D",
  "uniPairAddress": null,
  "tokenIndex": null,
  "pid": "0",
  "weight": 1,
  "weightDecimals": 0
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/masterchef-pool-balance?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiQ0hFRiIsImNoZWZBZGRyZXNzIjoiMHhEMzhhYmJBZUMwM2E5RkYyODdlRmM5YTVGMGQwNTgwRTA3MzM1RDFEIiwidW5pUGFpckFkZHJlc3MiOm51bGwsInRva2VuSW5kZXgiOm51bGwsInBpZCI6IjAiLCJ3ZWlnaHQiOjEsIndlaWdodERlY2ltYWxzIjowfSwibmV0d29yayI6IjEiLCJzbmFwc2hvdCI6IiIsImFkZHJlc3NlcyI6WyIweGZDQTVhMjdkNGNmRjEwNEZDMjc2ODk3Q0EzZjMyY0ZlRGM2ZjUwQkEiLCIweDU3N2JmYTA4OTgxODdjMTBiYmJiYjNkMDAxYzk0YWFmYjVjZmMwZTQiLCIweDA2OGU0OGU5ODRiODMzODdhZmU3NzI2MTQ5MTY3ODBhNzUzOTI5ZDkiXX0." %}

### [contract-call](https://snapshot.org/#/strategy/contract-call)

A lot of use cases are beyond regular LP/staking scope, for example calculating the balance of staked NFT or from a custom contract.&#x20;

The good news is, if there's a method in your contract that reads the balance of the staked token with a single call (interaction with the Smart Contract), you don't need to create a new strategy.&#x20;

Instead, use `contract-call` strategy, which allows **any contract method** to be used to calculate voter scores.&#x20;

{% hint style="info" %}
**As this is a more advanced strategy, don't hesitate to reach out to our support team on** [**Help Center**](https://help.snapshot.org/en/)**!**
{% endhint %}

**Strategy setup:**

```
{
  "symbol": "vBNT",
  "address": "0x892f481BD6E9d7D26aE365211D9B45175d5D00e4",
  "decimals": 18,
  "methodABI": {
    "name": "votesOf",
    "type": "function",
    "inputs": [
      {
        "name": "_voter",
        "type": "address",
        "internalType": "address"
      }
    ],
    "outputs": [
      {
        "name": "",
        "type": "uint256",
        "internalType": "uint256"
      }
    ],
    "stateMutability": "view"
  }
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/contract-call?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4MGUwOWZhYmI3M2JkM2FkZTBhMTdlY2MzMjFmZDEzYTE5ZTgxY2U4MiIsInN5bWJvbCI6IkNha2UiLCJkZWNpbWFscyI6MTgsIm1ldGhvZEFCSSI6eyJpbnB1dHMiOlt7ImludGVybmFsVHlwZSI6ImFkZHJlc3MiLCJuYW1lIjoiYWNjb3VudCIsInR5cGUiOiJhZGRyZXNzIn1dLCJuYW1lIjoiYmFsYW5jZU9mIiwib3V0cHV0cyI6W3siaW50ZXJuYWxUeXBlIjoidWludDI1NiIsIm5hbWUiOiIiLCJ0eXBlIjoidWludDI1NiJ9XSwic3RhdGVNdXRhYmlsaXR5IjoidmlldyIsInR5cGUiOiJmdW5jdGlvbiJ9fSwibmV0d29yayI6IjU2Iiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHgwMDljRjdiQzU3NTg0Yjc5OTgyMzZlZmY1MWI5OEExNjhEY2VBOUIwIl19" %}

[^1]: Automated Market Makers
