---
description: >-
  If none of the above scenarios work for your use case, you can use the
  customizable Strategies to leverage your own custom calculation mechanisms.
  Read on to learn more!
---

# Custom calculations

Snapshot provides several Voting strategies that allow you to use your own API to return user's Voting power or for example perform mathematical calculations on the results from existing Strategies.

{% hint style="info" %}
You can also create a new custom Voting or Validation strategy if none of the available solutions meet your needs. \
\
Have a look at the [create-a-strategy](../developer-guides/create-a-strategy/ "mention") section of this documentation to learn more!
{% endhint %}

### [api-v2](https://snapshot.org/#/strategy/api-v2)

This strategy allows off-chain data to be used as Voting power through calling a custom API endpoint to request the score for a set of addresses.

It's useful to use this strategy if your API can return the Voting power directly. It's network agnostic. &#x20;

**Strategy setup:**

<table><thead><tr><th width="214">Name</th><th width="121">Type</th><th width="278">Description</th><th>Default</th></tr></thead><tbody><tr><td><code>url</code></td><td><code>string</code></td><td>URL of the API endpoint</td><td><code>undefined</code></td></tr><tr><td><code>type</code></td><td><code>string</code></td><td>Type of the API endpoint ( <code>api-get</code> or <code>api-post</code> or <code>ipfs</code> or <code>json</code> )</td><td><code>api-get</code></td></tr><tr><td><code>additionalParams</code></td><td><code>string</code></td><td>Additional parameters for the API endpoint (optional)</td><td>``</td></tr></tbody></table>

If you are passing an **IPFS URL** use the following format:

```JSON
{
  "url": "ipfs://...",
  "type": "ipfs"
}
```

If you are passing a JSON URL use the following format:

```JSON
{
  "url": "https://...",
  "type": "json"
}
```

If you are passing an **API URL** use the following format:&#x20;

{% hint style="info" %}
All voter addresses will be passed in the query string.
{% endhint %}

```JSON
{
  "url": "https://...",
  "type": "api-get"
}
```

If you are passing a **API URL with POST** method use the following format:

```JSON
{
  "url": "https://...",
  "type": "api-post"
}
```

You can test it out in the **Playground on Snapshot:**

{% embed url="https://snapshot.org/#/playground/api-v2?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiQkFMIiwiYWRkcmVzcyI6IjB4YmExMDAwMDA2MjVhMzc1NDQyMzk3OGE2MGM5MzE3YzU4YTQyNGUzRCIsImRlY2ltYWxzIjoxOH0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHhlRDJiY0MzMTA0RGE1RjVmOGZBOTg4RDZlOWZBRmQ3NEFlNjJmMzE5IiwiMHgzYzRCOEM1MkVkNGMyOWVFNDAyRDljOTFGZkFlMURiMkJBZGQyMjhEIiwiMHhkNjQ5YkFDZkY2NmYxQzg1NjE4YzUzNzZlZTRGMzhlNDNlRTUzYjYzIiwiMHg3MjYwMjJhOWZlMTMyMmZBOTU5MEZCMjQ0YjgxNjQ5MzZiQjAwNDg5IiwiMHhjNjY2NWViMzlkMjEwNmZiMURCRTU0YmYxOTE5MEY4MkZENTM1YzE5IiwiMHg2ZWYyMzc2ZmE2ZTEyZGFiYjNhM2VkMGZiNDRlNGZmMjk4NDdhZjY4IiwiMHg4OTQ0NmFGMDM2NTJjNTI1N2RCNUM4RTRFODU0OTVFQjc1NDE5NmM1Il19" %}

### [math](https://snapshot.org/#/strategy/math)

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

Strategy used in the example: [multichain](https://snapshot.org/#/strategy/multichain)
