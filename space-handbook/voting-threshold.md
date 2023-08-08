---
description: Define criteria that users have to meet in order to be eligible to vote.
---

# Voting threshold

Suppose you want to restrict the ability to vote within your community for example to prevent bots from affecting the results or to prioritize members with higher stakes in your organization. In that case, you can do so by setting up Voting strategies or a combination of Voting and Validation strategies for your space.

To recap what Voting and Validation strategies are:

[Validation strategies](../user-guides/strategies/validation-strategies.md) are a way to define who is allowed to vote on a proposal or create a new one.&#x20;

[Voting strategies](../user-guides/strategies/voting-strategies.md) calculate how much Voting power each user has.

## Voting validation&#x20;

This solution is a combination of any Voting strategy/-ies and Voting validation.

Defining the required threshold of the user's Voting power can be set up simply and leverage the Voting strategies used in the Space.

Go to Space settings and open the **Voting** tab. At the bottom you can find the Validation section:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-24 at 15.53.41.png" alt=""><figcaption></figcaption></figure>

### Basic Voting validation

Select the [**Basic Voting validation**](../user-guides/strategies/validation-strategies.md#validation-strategy-example-basic)**.**

<figure><img src="../.gitbook/assets/Screenshot 2023-06-20 at 11.39.23.png" alt=""><figcaption></figcaption></figure>

This way you can easily define how much Voting power is required for the users to cast votes on Proposals in your Space. Voting power is calculated on the basis of the Voting strategies set for your Space.

For example, if your Voting strategy is [`erc20-balance-of`](https://snapshot.org/#/strategy/erc20-balance-of) and a user holds 20 tokens, their Voting power will be 20 and they will be eligible to vote with the Basic Validation set at 10.&#x20;

If they hold 5 tokens, they won't be able to cast a vote as it's < 10 VP.

### Gitcoin Passport Validation

Select the [**Gitcoin Passport Validation**](../user-guides/strategies/validation-strategies.md#validation-strategy-example-gitcoin-passport).

This Validation allows you to set requirements by checking the [Gitcoin Passport](https://passport.gitcoin.co/) stamps which serve as validation for the user’s identity and online reputation. You can select individual or multiple stamps that matter for your space. You can also decide if they need to meet all of these criteria or only one.

<figure><img src="../.gitbook/assets/Screenshot 2023-05-24 at 16.03.47.png" alt=""><figcaption></figcaption></figure>



## Voting strategies

It is also possible to set a required threshold directly through a Voting strategy.

{% hint style="warning" %}
We highly recommend the first approach of using a Validation strategy as it allows **higher flexibility and is easier to maintain** if the Voting strategies are changed in the Space settings.
{% endhint %}

### [b**alance-of-with-min**](https://snapshot.org/#/strategy/balance-of-with-min)&#x20;

{% hint style="info" %}
You can use it with ERC-20 and ERC-721 tokens.
{% endhint %}

The strategy specifies the minimum balance required for a single token held in the user's wallet.

Let's have a look at an example below. In order to be eligible to vote users are required to hold at least 20 DAI at the snapshot of proposal creation.

**Strategy setup:**

```
{
  "address": "0x6b175474e89094c44da98b954eedeac495271d0f",
  "symbol": "DAI",
  "decimals": 18,
  "minBalance": 20
}
```

{% hint style="info" %}
If you are using this strategy for an NFT, make sure to set the **`decimals`** to **0** (zero).
{% endhint %}

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/balance-of-with-min?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4NmIxNzU0NzRlODkwOTRjNDRkYTk4Yjk1NGVlZGVhYzQ5NTI3MWQwZiIsInN5bWJvbCI6IkRBSSIsImRlY2ltYWxzIjoxOCwibWluQmFsYW5jZSI6MjB9LCJuZXR3b3JrIjoiMSIsInNuYXBzaG90IjoiIiwiYWRkcmVzc2VzIjpbIjB4YTQ3OGMyOTc1YWIxZWE4OWU4MTk2ODExZjUxYTdiN2FkZTMzZWIxMSIsIjB4ZUY4MzA1RTE0MGFjNTIwMjI1REFmMDUwZTJmNzFkNWZCY0M1NDNlNyIsIjB4OUI4ZThkRDkxNTEyNjBjMjFDQjZEN2NjNTkwNjdjZDhERjMwNkQ1OCIsIjB4MzhDMDAzOTI0N0EzMUYzOTM5YmFFNjVlOTUzNjEyMTI1Y0I4ODI2OCJdfQ.." fullWidth="false" %}

### [balance-of-with-thresholds](https://snapshot.org/#/playground/balance-of-with-thresholds)

{% hint style="info" %}
You can use it with ERC-20 and ERC-721 tokens.
{% endhint %}

This strategy allows you to define multiple thresholds and allocate Voting power at each level.&#x20;

In the example below, whoever holds less than 1 unit of the token will have **0** Voting power.

Users holding more than 1 but less than 4 units of the token will have **1** Voting power.

The maximum Voting power per user will be fixed at 4 no matter how much of the token they own.&#x20;

**Strategy setup:**

```
{
  "address": "0xf87e31492faf9a91b02ee0deaad50d51d56d5d4d",
  "symbol": "LAND",
  "decimals": 0,
  "thresholds": [
    { "threshold": 1, "votes": 1 },
    { "threshold": 4, "votes": 2 },
    { "threshold": 11, "votes": 3 },
    { "threshold": 25, "votes": 4 }
  ]
}
```

{% hint style="info" %}
To achieve 1 vote per wallet, simply keep the line `{ "threshold": 1, "votes": 1 }` under the `thresholds` param, and remove other keys and values. &#x20;
{% endhint %}

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/balance-of-with-thresholds?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4QkM0Q0EwRWRBNzY0N0E4YUI3QzIwNjFjMkUxMThBMThhOTM2ZjEzRCIsInN5bWJvbCI6IkJBWUMiLCJkZWNpbWFscyI6MCwidGhyZXNob2xkcyI6W3sidGhyZXNob2xkIjoxLCJ2b3RlcyI6MX0seyJ0aHJlc2hvbGQiOjQsInZvdGVzIjoyfSx7InRocmVzaG9sZCI6MTEsInZvdGVzIjozfSx7InRocmVzaG9sZCI6MjUsInZvdGVzIjo0fV19LCJuZXR3b3JrIjoiMSIsInNuYXBzaG90IjoiIiwiYWRkcmVzc2VzIjpbIjB4ZWQ0NzAxNWJiODA4MGI5Mzk5ZjlkMGRkZmM0MjdiOWNlZTJjYWFiMSIsIjB4ZjU2MzQ1MzM4Y2I0Y2RkYWY5MTVlYmVmM2JmZGU2M2U3MGZlMzA1MyIsIjB4N2IxNWU2YzQzOWIyN2E1NTNiNjVhOTkwNGNlNTcxZGE2NjkxYTBmYiIsIjB4OGQyZjNhNzZhNzZmMDU1ZDYyYTkzMTY3OGFiMTZiMDQyZTdiYWRlYiJdfQ.." %}

### [e**rc20-with-balance**](https://snapshot.org/#/strategy/erc20-with-balance)

{% hint style="info" %}
You can use it with ERC-20 and ERC-721 tokens.
{% endhint %}

**erc20-with-balance** in its simplest form assigns **1 vote** to wallets holding **any** balance of the token.   Regardless of how big the balance is, the VP is always the same and is at 1 VP. If the wallet doesn't hold any token, the VP is 0.

{% hint style="info" %}
This allows you to poll your community without referencing the number of tokens or NFTs they hold, **each address will have 1VP**.
{% endhint %}

Now, to use this strategy to set a voting threshold you can add an optional parameter `minBalance` and define the minimum required balance which will give the user the **eligibility to vote** and **1 Voting power**. The parameter value is set to 0 by default.&#x20;

**Strategy setup:**

```
{
  "address": "0x84cA8bc7997272c7CfB4D0Cd3D55cd942B3c9419",
  "symbol": "Rome",
  "decimals": 18,
  "minBalance": 10
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/erc20-with-balance?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4ODRjQThiYzc5OTcyNzJjN0NmQjREMENkM0Q1NWNkOTQyQjNjOTQxOSIsInN5bWJvbCI6IlJvbWUiLCJkZWNpbWFscyI6MTgsIm1pbkJhbGFuY2UiOjEwfSwibmV0d29yayI6IjEiLCJzbmFwc2hvdCI6IjE3MzM1ODIyIiwiYWRkcmVzc2VzIjpbIjB4MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMGJhZGRhZCIsIjB4YTQ3OGMyOTc1YWIxZWE4OWU4MTk2ODExZjUxYTdiN2FkZTMzZWIxMSIsIjB4ZUY4MzA1RTE0MGFjNTIwMjI1REFmMDUwZTJmNzFkNWZCY0M1NDNlNyIsIjB4QkEyRTdGZWQ1OTdmZDBFM2U3MGY1MTMwQmNEYmJGRTA2YkI5NGZlMSIsIjB4NEM3OTA5ZDZGMDI5YjNhNTc5ODE0M0M4NDNGNGY4ZTUzNDFhMzQ3MyIsIjB4ODRjQThiYzc5OTcyNzJjN0NmQjREMENkM0Q1NWNkOTQyQjNjOTQxOSIsIjB4NzJhYzE3NjBkYWY1Mjk4NjQyMWIxNTUyYmRjYTA0NzA3ZTc4OTUwZSJdfQ.." %}

### [math](https://snapshot.org/#/strategy/math) & [multichain](https://snapshot.org/#/strategy/multichain)

{% hint style="info" %}
You can use the `math` strategy flexibly with various tokens and networks. This example demonstrates how to set a threshold taking into account tokens on different chains.
{% endhint %}

`Math` strategy is powerful in its composability. It allows you to apply common mathematical operations to the outputs of Voting strategies.

As an example, you can take a square root of the Voting power calculated by [erc20-balance-of](https://snapshot.org/#/strategy/erc20-balance-of), or the lower (`min`) value out of two different Voting strategies. You can see all possibilities on the [strategy page](https://snapshot.org/#/strategy/math).

#### How to set it up for a multichain scenario?

If the Voting power calculated for your space is based on tokens on different chains and you want to set a minimum threshold defining if a user is eligible to vote, you can use the `a-if-lt-b` operand. Don't worry if it sounds cryptic, we will go through it step by step.&#x20;

| Operation   | Operand count | Description               |
| ----------- | ------------- | ------------------------- |
| `a-if-lt-b` | 3             | (x, a, b) = x < b ? a : x |

Let's look at the formula first: `(x, a, b) = x < b ? a : x`, where:&#x20;

* **x** - sum of Voting power calculated by the two Voting strategies on chains `137` and `1` (as per the example below)
* **a** - first constant, in our case it's **0**
* **b** - first constant, in our case it's **100**

**Strategy setup:**

```
{
  "symbol": "GHST",
  "operands": [
    {
      "type": "strategy",
      "strategy": {
        "name": "multichain",
        "params": {
          "strategies": [
            {
              "name": "erc20-balance-of",
              "network": "137",
              "params": {
                "address": "0x385eeac5cb85a38a9a07a70c73e0a3271cfb54a7",
                "decimals": 18
              }
            },
            {
              "name": "erc20-balance-of",
              "network": "1",
              "params": {
                "address": "0x3f382dbd960e3a9bbceae22651e88158d2791550",
                "decimals": 18
              }
            }
          ]
        }
      }
    },
    {
      "type": "constant",
      "value": 0
    },
    {
      "type": "constant",
      "value": 1
    }
  ],
  "operation": "a-if-lt-b"
}
```

The algorithm will check if **x** is smaller than **b**, the second constant:

* if it's below **b**, the final Voting power will be set to **a,** first constant -> **0**
* if it's equal to and higher than **b**, the final Voting power will be set to **x**, the sum of result from the Voting strategies

**As you can see we can easily define what is the minimum Voting power (our example: 100) coming from different chains that is required for the user to vote!**&#x20;

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/math?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiR0hTVCIsIm9wZXJhbmRzIjpbeyJ0eXBlIjoic3RyYXRlZ3kiLCJzdHJhdGVneSI6eyJuYW1lIjoibXVsdGljaGFpbiIsInBhcmFtcyI6eyJzdHJhdGVnaWVzIjpbeyJuYW1lIjoiZXJjMjAtYmFsYW5jZS1vZiIsIm5ldHdvcmsiOiIxMzciLCJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4Mzg1ZWVhYzVjYjg1YTM4YTlhMDdhNzBjNzNlMGEzMjcxY2ZiNTRhNyIsImRlY2ltYWxzIjoxOH19LHsibmFtZSI6ImVyYzIwLWJhbGFuY2Utb2YiLCJuZXR3b3JrIjoiMSIsInBhcmFtcyI6eyJhZGRyZXNzIjoiMHgzZjM4MmRiZDk2MGUzYTliYmNlYWUyMjY1MWU4ODE1OGQyNzkxNTUwIiwiZGVjaW1hbHMiOjE4fX1dfX19LHsidHlwZSI6ImNvbnN0YW50IiwidmFsdWUiOjB9LHsidHlwZSI6ImNvbnN0YW50IiwidmFsdWUiOjF9XSwib3BlcmF0aW9uIjoiYS1pZi1sdC1iIn0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIxNzM0MjkzNyIsImFkZHJlc3NlcyI6WyIweDVDNTJjQzdjOTZiREU4NTk0ZTVCNzdENWI3NmQwNDJDQjVGYUU1ZjIiLCIweDREMTlDMGE1MzU3YkM0OGJlMDAxNzA5NWQzQzg3MUQ5YUZDM0YyMWQiLCIweGY1OTg2OTc1M2Y0MURiNzIwMTI3Q2ViOERiQjhhZkFGODkwMzBEZTQiXX0." %}

### 5. [holds-tokens](https://snapshot.org/#/strategy/holds-tokens)

{% hint style="info" %}
You can use it with ERC-20 and ERC-721 tokens, on multiple networks.
{% endhint %}

If you want to require users to hold specific tokens in order to be eligible to vote you can use the `holds-tokens` strategy.&#x20;

The minimum balance for each token can be customized.

Users who meet the criteria will receive **1 Voting power** regardless of the total value of the tokens they hold.

{% hint style="warning" %}
Note, that the `minBalance` parameter is exclusive. It means that when set to **1**, the user has to hold more than **1** of the specified token in order to vote.


{% endhint %}

**Strategy setup:**

```
{
  "symbol": "XYZ",
  "tokenAddresses": [
    {
      "address": "0x57f1887a8BF19b14fC0dF6Fd9B2acc9Af147eA85",
      "network": "1",
      "decimals": 0,
      "minBalance": 0
    },
    {
      "address": "0xaC4255eC6885E50352A1957062ac418c2CC94e27",
      "network": "137",
      "decimals": 0,
      "minBalance": 0
    }
  ]
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/holds-tokens?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiQkFMIiwiYWRkcmVzcyI6IjB4YmExMDAwMDA2MjVhMzc1NDQyMzk3OGE2MGM5MzE3YzU4YTQyNGUzRCIsImRlY2ltYWxzIjoxOH0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHhDNWUzODIzM0NjMEQ3Q0ZmOTM0MGU2MTM5MzY3YUJBNDk4RUM5YjE4IiwiMHgyMDA5YTc1MmE1MEQzQ0RlNDg2ZDdiNTkyMTk0NDM3N0I3MjlFNzQ3IiwiMHg3YjE1ZTZjNDM5YjI3YTU1M2I2NWE5OTA0Y2U1NzFkYTY2OTFhMGZiIiwiMHg4ZDJmM2E3NmE3NmYwNTVkNjJhOTMxNjc4YWIxNmIwNDJlN2JhZGViIiwiMHhFRGU2NGE1NzFDRmU5OEI5MzYyNzFCOTM1YTk1NTYyMGYzODdFMDVBIl19" %}

