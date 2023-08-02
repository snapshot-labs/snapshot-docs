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

Whales can influence not only currency markets but also the governance process of web3 communities. With the large holdings, their sheer Voting power can oftentimes swing a proposal for their advantage. This leads to outcomes that are not welcomed by the community, poses a threat to taking the Treasury over, and also to lowering community participation in the vote as its members don't see the point in voting knowing that one wallet can decide on its outcome.

Let's have a look at different setups that will allow your space to minimize the power of whales.

## Voting types

You can predefine the [Voting type](#user-content-fn-1)[^1] that all proposals in your space will use. In the case of the anti-whale approach, the best solution is the Quadratic Voting type.

### 1. Quadratic voting

Snapshot's Quadratic Voting type is based on the Quadratic Funding model and was developed to target shortcomings of the traditional quadratic calculation taking the root square of a value, in our case - Voting power. Unlike the traditional quadratic calculation, it can handle values as tiny as 0.000001 and include them in the voting process.

You can set it up for all proposals in your Space by heading to the **Voting** tab in the Space settings and selecting the desired Voting type in the **Type** field:

<figure><img src="../.gitbook/assets/Screenshot 2023-06-12 at 15.26.16.png" alt=""><figcaption></figcaption></figure>

#### **Let's have a look at an example:**

There are 11 voters and three choices, A,B and C:

* John with 100 SMS tokens
* Bob with 98 SMS tokens
* 9 Marias with 3 SMS tokens each

\-> John allocates all his 95 tokens to A and 5 tokens to B&#x20;

\-> Bob allocates half his 90 tokens to B and 8 tokens to C&#x20;

\-> All the 9 Marias allocate their 3 tokens to C

This results in:

* A having 37 SMS or 16.44%&#x20;
* B having 56 SMS or 24.87%&#x20;
* C having 132 SMS or 58.69%

#### **How was it calculated?**

1. First, we need to calculate the **individual square root contributions** for each choice:&#x20;

* A: the square root of John's 95 tokens is √95 ≈ **9.75.**
* B: the square root of John's 5 tokens is √5 ≈ **2.24**, and the square root of Bob's 90 tokens is √95 ≈ **9.75.**
* C: the square root of Bob's 8 tokens is √8 ≈ **2.83**, and each Maria contributes √3 ≈ 1.73, so 9 Marias contribute **15.59** in total

2. Now, we **add up the square root** contributions for each choice and **square the result**:

* A: we square the 9.75, so A gets 9.75^2 = **95.06 SMS.**
* B: we add 2.24 and 9.75, giving us 11.99, and square it, so B gets 11.99^2 = **143.76 SMS.**
* C, we add 2.83 and 15.59, giving us 18.42, and square it, so C gets 18.42^2 = **339.29 SMS.**

The total amount of SMS is 95.06 + 143.76 + 339.29 = **578.11.**

So the percentages for each choice is:&#x20;

* A: 95.06 / 578.11 = 16.44%
* B: 143.76 / 578.11 = 24.87%
* C: 339.29 / 578.11 = 58.69%

3. As a last step we **match these percentages with the total voting power** of 225 SMS:&#x20;

* A: 16.44% of 225 = **37 SMS**
* B: 24.87% of 225 = **56 SMS**
* C: 58.69% of 225 = **132 SMS**

{% hint style="info" %}
All in all you don't have to understand each step of the calculation, yet it should give you an idea how John with 100 SMS tokens was not able to push through his choice despite having the majority of Voting power in the group as Quadratic Funding model emphasises the **number of individual contributors** rather than the amount contributed.
{% endhint %}

{% hint style="danger" %}
This Voting type may encourage the whales to create multiple wallets and split their holdings among them. Therefore it's important to also implement a mechanism providing Sybil Resistance. \
\
**Read more** [**here**](sybil-resistance-scam-and-spam-prevention.md)**!**
{% endhint %}

## Voting strategies

### 1. [balance-of-with-thresholds](https://snapshot.org/#/strategy/balance-of-with-thresholds)

You can think of it as creating multiple buckets which will determine the Voting power of an individual address. To put it in the simplest way, imagine that:

* users who hold less than 5 tokens will have **0** Voting power
* users who hold from 5 to 10 tokens will have **1** Voting power
* users who hold from 10 to 20 tokens will have **2** Voting power
* users who hold more than 20 tokens will have **5** Voting power

As you can see, you are able to set various thresholds which will fix user's Voting power at a specific level. This way whales who may have large holdings, for example 1000 tokens, will not get more than **5** Voting power.&#x20;

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

This strategy executes a chosen Voting strategy and applies algorithms to its result to reduce the impact of big wallets on the vote.&#x20;

{% hint style="info" %}
This strategy requires understanding some of the calculations shown below. If you have issues with setting it up don't hesitate to [create a ticket on Discord](https://discord.com/channels/707079246388133940/1090290400943677440)!
{% endhint %}

In practice, the strategy sets a **soft restriction on the voting threshold** by giving limited incentive to the voter below threshold by **moderately increasing the voting power** of voters and **reducing the impact** of whales as token amount increases, keeping the gap in voting power within a relatively moderate range.&#x20;

As an example, assuming our threshold is **5**:

* if user's Voting power is below or equal to 5, their final Voting power will be moderately increased
* if user's Voting power is above 5, their final Voting power will be reduced (the higher the Voting power, the more increased it will be)

The following algorithm is applied to the result of the configured Voting strategy:

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
