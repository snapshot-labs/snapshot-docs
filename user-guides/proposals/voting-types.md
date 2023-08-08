---
description: Learn more about the different voting schemes on Snapshot.
---

# Voting types

{% hint style="info" %}
Snapshot supports a number of different voting types and we plan to support many more in the future. If you would like to request a new voting type, please open a feature request [here](https://features.snapshot.org/feature-requests) :pray:&#x20;
{% endhint %}

## What is a voting type?

Voting type defines how users can cast their votes and how the final result is calculated.

Do not mistake it with the voting strategy though - a [voting strategy](../strategies/voting-strategies.md) is used to calculate the **individual voting power** of a user while the voting type calculates the **outcome of the proposal**.

Voting type is defined in the space settings or at the level of an individual proposal (unless it has been already defined in the space settings) and can allow the users to:&#x20;

* Choose only **one option** - [#single-choice-voting](voting-types.md#single-choice-voting "mention")
* Spread their votes over **multiple options** - [#weighted-voting](voting-types.md#weighted-voting "mention")
* **Approve** a certain number of options - [#approval-voting](voting-types.md#approval-voting "mention")
* Spread their votes over multiple options using the [**quadratic voting**](https://en.wikipedia.org/wiki/Quadratic\_voting) **formula** - [#quadratic-voting](voting-types.md#quadratic-voting "mention")
* Rank the different choices in their **order of preference** - [#ranked-choice-voting-instant-runoff-voting](voting-types.md#ranked-choice-voting-instant-runoff-voting "mention")
* **Abstain** from voting while still participating in quorum - [#basic-voting](voting-types.md#basic-voting "mention")

Let's have a look at each voting type in the next section.

## Voting types

### Single choice voting

Each user can select only one option. The results will reflect these votes as percentages of the total voting power of all voting participants cast on the specific choice.&#x20;

Ideal for choosing one option from many.\
\
**Pros**: Most simple and common voting type which is easy to set up and use.\
**Cons**: Voters can pick only one option.

👉 [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x02c3fcd64e86157d07c88e5a715ac08f57655917f8bfd5be30a99092136511ec)

<figure><img src="../../.gitbook/assets/image (8) (2) (1).png" alt=""><figcaption></figcaption></figure>

### Weighted voting

Each user can spread their voting power across any number of choices, from one to all. Their voting power will be divided between their chosen options according to how much weight they attribute to each option by increasing or decreasing the voting power fraction.

**Pros**: Allows voters to express support for more than one option and specify how much they support each of them.\
**Cons**: Requires more time and adds complexity to the voting process.

This voting method was first introduced by Float Protocol with [Scattershot](https://github.com/FloatProtocol/scattershot) (a fork of Snapshot).

:point\_right: [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0xf93f1ac80e22cc930b1eef1d20bd34671ccc33b88b04695479c9de364451d77f)

<figure><img src="../../.gitbook/assets/image (4) (4).png" alt=""><figcaption></figcaption></figure>

### Approval voting

Each user can select (_approve_) any number of choices, each selected choice will receive equal voting power, i.e. if user selects two choices, each choice will receive the total voting power of the user.

**Pros**: Ask for approval of several decisions in a single proposal.\
**Cons**: There is no way to manifest _how much_ you support each choice. It’s a simple yes or no.

:point\_right: [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x08c3bd2960700525770a1d634f8599ba967e55fcc05b6c1649d984d88253769d)

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Quadratic voting

Snapshot's Quadratic Voting (QV) type goes beyond the conventional approach of simply calculating the square root of each voter's voting power. It presents a more nuanced and democratic framework for decision-making.

One of the main features of our QV type is its **emphasis on the number of individual voters** rather than the size of their voting power. By doing so, it ensures that every voice counts, thereby enhancing collective decision-making and preventing power concentration.

Additionally, Snapshot's QV type provides voters with the flexibility to **distribute their voting power across multiple choices**. This feature allows for a more precise representation of a voter's diverse opinions, all without any additional cost.

Drawing key principles from the Quadratic Funding model, our QV type **fosters greater participation and effectively balances influence**. It represents a significant advancement over simpler voting mechanisms that rely on basic square root calculations of voting power.

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
All in all, you don't have to understand each step of the calculation. Yet, it should give you an idea of how Alice with 9 tokens was not able to push through his choice despite having the majority of Voting power in the group as our QV model emphasizes the **number of individual contributors** rather than the amount contributed.
{% endhint %}

{% hint style="danger" %}
This Voting type may encourage the whales to create multiple wallets and split their holdings among them. Therefore it's important to also implement a mechanism providing Sybil Resistance. \
\
**Read more** [**here**](../../space-handbook/sybil-resistance-scam-and-spam-prevention.md)**!**
{% endhint %}

**Pros**: Dilutes the whales' voting power in favor of smaller holders. Individuals will matter more than the number of tokens. \
**Cons**: This voting type needs to be accompanied by a [Sybil-resistance mechanism](../strategies/validation-strategies.md) that prevents whales from splitting funds across different wallets.&#x20;

:point\_right: [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x21f64875abbca71762a980efae43ab62b546d54f19a208d0e61a5d7cee571a35)

<figure><img src="../../.gitbook/assets/image (6) (2) (1).png" alt=""><figcaption></figcaption></figure>

### Ranked choice voting (Instant Runoff Voting)

Each user has to rank all choices in a desired order.&#x20;

In the **first step** votes are counted for each voter's number one choice. If a choice receives more than 50% votes (cast on number one choices of each user), that choice wins. The result will show the percentages reflecting how users voted for their **first choice only**.

In the **second step** if the first-choice candidate doesn't get over 50% of the total votes the choice with the **fewest** number one votes is **eliminated**. Voters who had chosen the defeated choice as number one now have their number two choice **counted as their number one** choice.&#x20;

The process continues over multiple rounds until a choice has more than half (> 50%) of the total votes.&#x20;

For more details, read [this discussion](https://github.com/snapshot-labs/snapshot/discussions/1624).

{% hint style="info" %}
Some options will show up as if they had **not received any votes** because they were **eliminated** in the ranked-choice voting process.
{% endhint %}

**Pros**: Favors the option with the strongest support and reduces wasted votes. \
**Cons**: Complex to understand. Will only determine one winner, doesn’t work well to select 2 or more winning options.

:point\_right: [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x5003da0f03e718b461e53fe10a998b60172e2e108472153282fcef781c300f23)

<figure><img src="../../.gitbook/assets/image (16) (3) (1).png" alt=""><figcaption></figcaption></figure>

### Basic voting

Each user can select one of three options: `For`, `Against`, `Abstain`.

The votes cast on the `Abstain` choice are counted in calculating if the necessary quorum has been reached for a proposal to pass.

**Pros**: Results are easy to interpret and hard to contest.\
**Cons**: Choices are predefined and cannot be edited.&#x20;

:point\_right: [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x38c654c0f81b63ea1839ec3b221fad6ecba474aa0c4e8b4e8bc957f70100e753)

<figure><img src="../../.gitbook/assets/image (19) (1).png" alt=""><figcaption></figcaption></figure>
