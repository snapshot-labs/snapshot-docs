---
description: >-
  Minimize the power of large token holders and encourage your community to take
  part in the vote!
---

# Anti-whale

## What is a whale?

> A cryptocurrency whale, more commonly known as a "crypto whale" or just a "whale," is a cryptocurrency community term that refers to individuals or entities that hold large amounts of cryptocurrency. Whales own enough cryptocurrency to influence currency markets.\
> \
> [_https://www.investopedia.com/terms/b/bitcoin-whale.asp_](https://www.investopedia.com/terms/b/bitcoin-whale.asp)

Whales can influence not only currency markets but also the governance process of web3 communities. With the large holdings, their sheer Voting Power can oftentimes swing a proposal for their advantage. This leads to outcomes that are not welcomed by the community, poses a threat to taking the Treasury over, and also to lowering community participation in the vote as its members don't see the point in voting knowing that one wallet can decide on its outcome.

Let's have a look at different setups that will allow your space to minimize the power of whales.

## Voting types

You can predefine the [Voting type](#user-content-fn-1)[^1] that all proposals in your space will use. In the case of the anti-whale approach, the best solution is the Quadratic Voting type.

### 1. Quadratic voting

Snapshot's Quadratic Voting (QV) type goes beyond the conventional approach of simply calculating the square root of each voter's voting power. It presents a more nuanced and democratic framework for decision-making.

One of the main features of our QV type is its **emphasis on the number of individual voters** rather than the size of their voting power. By doing so, it ensures that every voice counts, thereby enhancing collective decision-making and preventing power concentration.

Additionally, Snapshot's QV type provides voters with the flexibility to **distribute their voting power across multiple choices**. This feature allows for a more precise representation of a voter's diverse opinions, all without any additional cost.

Drawing key principles from the Quadratic Funding model, our QV type **fosters greater participation and effectively balances influence**. It represents a significant advancement over simpler voting mechanisms that rely on basic square root calculations of voting power.

You can set it up for all proposals in your Space by heading to the **Voting** tab in the Space settings and selecting the desired Voting System in the **Type** field:

<figure><img src="../.gitbook/assets/Screenshot 2023-06-12 at 15.26.16.png" alt=""><figcaption></figcaption></figure>

#### **Let's have a look at an example:**

Let's consider there are 3 voters and two choices, A and B:

* Alice with 9 tokens
* Bob with 4 tokens
* Maria with 1 token
* John with 1 token

Here's how they allocate their tokens:

* Alice allocates all her 9 tokens to A
* Bob allocates all his 4 tokens to B
* Maria allocates her 1 token to B
* John allocates his 1 token to B

This results in:

* A having 9 tokens
* B having 6 tokens

Now, let's calculate the individual square root contributions for each choice:

* A: the square root of Alice's 9 tokens is √9 = 3.
* B: the square root of Bob's 4 tokens is √4 = 2, the square root of Maria's 1 token is √1 = 1, and the square root of John's 1 token is √1 = 1.

Next, we add up the square root contributions for each choice and square the result:

* A: we square the 3, so A gets 3^2 = 9.
* B: we add 2, 1, and 1, giving us 4, and square it, so B gets 4^2 = 16.

The total amount of tokens is 9 + 16 = 25.

So the percentages for each choice are:

* A: 9 / 25 = 36%
* B: 16 / 25 = 64%

As a last step, we match these percentages with the total voting power of 14 tokens:

* A: 36% of 15 = 5.4 tokens
* B: 64% of 15 = 9.6 tokens

{% hint style="info" %}
All in all you don't have to understand each step of the calculation, yet it should give you an idea how John with 100 SMS tokens was not able to push through his choice despite having the majority of Voting Power in the group as Quadratic Funding model emphasizes the **number of individual contributors** rather than the amount contributed.
{% endhint %}

{% hint style="danger" %}
This Voting System may encourage the whales to create multiple wallets and split their holdings among them. Therefore it's important to also implement a mechanism providing Sybil Resistance. \
\
**Read more** [**here**](sybil-resistance-scam-and-spam-prevention.md)**!**
{% endhint %}

## Voting strategies

### 1. [balance-of-with-thresholds](https://snapshot.org/#/strategy/balance-of-with-thresholds)

You can think of it as creating multiple buckets which will determine the Voting Power of an individual address. To put it in the simplest way, imagine that:

* users who hold less than 5 tokens will have **0** Voting Power
* users who hold from 5 to 10 tokens will have **1** Voting Power
* users who hold from 10 to 20 tokens will have **2** Voting Power
* users who hold more than 20 tokens will have **5** Voting Power

As you can see, you are able to set various thresholds which will fix user's Voting Power at a specific level. This way whales who may have large holdings, for example 1000 tokens, will not get more than **5** Voting Power.&#x20;

This way the voting can be more reflective of the public opinion.

**Strategy setup:**

```
{
  "address": "0xf87e31492faf9a91b02ee0deaad50d51d56d5d4d",
  "symbol": "LAND",
  "decimals": 0,
  "thresholds": [
    { "threshold": 5, "votes": 1 },
    { "threshold": 10, "votes": 2 },
    { "threshold": 20, "votes": 5 }
  ]
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/balance-of-with-thresholds?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4Zjg3ZTMxNDkyZmFmOWE5MWIwMmVlMGRlYWFkNTBkNTFkNTZkNWQ0ZCIsInN5bWJvbCI6IkxBTkQiLCJkZWNpbWFscyI6MCwidGhyZXNob2xkcyI6W3sidGhyZXNob2xkIjo1LCJ2b3RlcyI6MX0seyJ0aHJlc2hvbGQiOjEwLCJ2b3RlcyI6Mn0seyJ0aHJlc2hvbGQiOjIwLCJ2b3RlcyI6NX1dfSwibmV0d29yayI6IjEiLCJzbmFwc2hvdCI6IjE3Mzc4MjU5IiwiYWRkcmVzc2VzIjpbIjB4ZWQ0NzAxNWJiODA4MGI5Mzk5ZjlkMGRkZmM0MjdiOWNlZTJjYWFiMSIsIjB4ZjU2MzQ1MzM4Y2I0Y2RkYWY5MTVlYmVmM2JmZGU2M2U3MGZlMzA1MyIsIjB4N2IxNWU2YzQzOWIyN2E1NTNiNjVhOTkwNGNlNTcxZGE2NjkxYTBmYiIsIjB4OGQyZjNhNzZhNzZmMDU1ZDYyYTkzMTY3OGFiMTZiMDQyZTdiYWRlYiJdfQ.." %}

### 2.[ anti-whale](https://snapshot.org/#/strategy/anti-whale)

This strategy executes a chosen Voting Strategy and applies algorithms to its result to reduce the impact of big wallets on the vote.&#x20;

{% hint style="info" %}
This strategy requires understanding some of the calculations shown below. If you have issues with setting it up contact our support on [Help Center](https://help.snapshot.org/en/)
{% endhint %}

In practice, the strategy sets a **soft restriction on the voting threshold** by giving limited incentive to the voter below threshold by **moderately increasing the voting power** of voters and **reducing the impact** of whales as token amount increases, keeping the gap in voting power within a relatively moderate range.&#x20;

As an example, assuming our threshold is **5**:

* if user's Voting Power is below or equal to 5, their final Voting Power will be moderately increased
* if user's Voting Power is above 5, their final Voting Power will be reduced (the higher the Voting Power, the more increased it will be)

The following algorithm is applied to the result of the configured Voting Strategy:

```
If result > antiWhale.threshold
  result = antiWhale.inflectionPoint * ( result / antiWhale.inflectionPoint ) ^ antiWhale.exponent

If result <= antiWhale.threshold {
  thresholdMultiplier = ( antiWhale.inflectionPoint * ( antiWhale.threshold / antiWhale.inflectionPoint )^ antiWhale.exponent ) / antiWhale.threshold

  result = result * thresholdMultiplier
}
```

#### **Parameters**

**`antiWhale.threshold`** - point at which the `antiWhale` takes effect.&#x20;

{% hint style="info" %}
Results not greater than the **threshold** will be treated with a **static multiplier.** This is to reduce infinite incentive for **multiple wallet** exploits.
{% endhint %}

* Default: 1625
* Lower limit: > 0 - set to default if ≤ 0

**`thresholdMultiplier`** - the multiplier at which all results below `antiWhale.threshold` are multiplied.

**`antiWhale.inflectionPoint`** - point at which the output matches the result.&#x20;

\-> Results **less** than this will **increase** output.&#x20;

\-> Results **greater** than the inflection point will decrease output.

* Default: 6500
* Lower limit: > 0 - set to default if ≤ 0
* Must be bigger or equal to `antiWhale.threshold`. Otherwise will be same as `antiWhale.threshold`

**`antiWhale.exponent`** - the exponent is responsible for the antiWhale effect.&#x20;

\-> Must be ≤ 1, or else it will have a pro-whale effect.&#x20;

\-> Must be ＞0, or else it will cause total voting power to trend to 0. Look at the example below to understand its effect.

{% hint style="info" %}
**Example**

* random value = 5
* exponent A = 0.5
* exponent B = 1.5

\
Calculation A: 5 ^ 0.5 \~= 2.236

Calculation B: 5 ^ 1.5 \~= 11.18\
\
As you can see exponent **lower than 1 will reduce** the original random value while exponent **bigger than 1 will increase it.**
{% endhint %}

* Default: 0.5.
* Upper limit: 1.
* Lower limit: > 0 - set to default if ≤ 0.

**`log`:** Boolean flag to enable or disable logging to the console (used for debugging purposes during development)

**Strategy setup:**

```
{
  "symbol": "ANTI",
  "strategy": {
    "name": "erc20-balance-of",
    "params": {
      "address": "0x579cea1889991f68acc35ff5c3dd0621ff29b0c9",
      "symbol": "IQ",
      "decimals": 18
    }
  },
  "antiWhale": {
    "inflectionPoint": 1000,
    "threshold": 250,
    "exponent": 0.5
  },
  "log": true
}
```

[^1]: [Voting ](../user-guides/proposals/voting-types.md)[type](../user-guides/proposals/voting-types.md) defines how users can cast their votes and how the final result is calculated.

    Do not mistake it with the voting strategy though - a [voting strategy](../user-guides/strategies/voting-strategies.md) is used to calculate the **individual voting power** of a user while the voting system calculates the **outcome of the proposal**.
