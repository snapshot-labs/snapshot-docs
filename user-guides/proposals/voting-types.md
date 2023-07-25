---
description: Learn more about the different voting schemes on Snapshot.
---

# Voting systems

{% hint style="info" %}
Snapshot supports a number of different voting systems and we plan to support many more in the future. If you would like to request a new voting type, please open a feature request [here](https://features.snapshot.org/feature-requests) :pray:&#x20;
{% endhint %}

## What is a voting system?

Voting system defines how users can cast their votes and how the final result is calculated.

Do not mistake it with the voting strategy though - a [voting strategy](../strategies/voting-strategies.md) is used to calculate the **individual voting power** of a user while the voting system calculates the **outcome of the proposal**.

Voting system is defined in the space settings or at the level of an individual proposal (unless it has been already defined in the space settings) and can allow the users to:&#x20;

* Choose only **one option** - [#single-choice-voting](voting-types.md#single-choice-voting "mention")
* Spread their votes over **multiple options** - [#weighted-voting](voting-types.md#weighted-voting "mention")
* **Approve** a certain number of options - [#approval-voting](voting-types.md#approval-voting "mention")
* Spread their votes over multiple options using the [**quadratic voting**](https://en.wikipedia.org/wiki/Quadratic\_voting) **formula** - [#quadratic-voting](voting-types.md#quadratic-voting "mention")
* Rank the different choices in their **order of preference** - [#ranked-choice-voting-instant-runoff-voting](voting-types.md#ranked-choice-voting-instant-runoff-voting "mention")
* **Abstain** from voting while still participating in quorum - [#basic-voting](voting-types.md#basic-voting "mention")

Let's have a look at each voting system in the next section.

## Voting systems types

### Single choice voting

Each user can select only one option. The results will reflect these votes as percentages of the total voting power of all voting participants cast on the specific choice.&#x20;

Ideal for choosing one option from many.\
\
**Pros**: Most simple and common voting system which is easy to set up and use.\
**Cons**: Voters can pick only one option.

👉 [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x02c3fcd64e86157d07c88e5a715ac08f57655917f8bfd5be30a99092136511ec)

<figure><img src="../../.gitbook/assets/image (8) (2).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Quadratic voting

Snapshot's Quadratic Voting system is more than a simplistic square root calculation of each voter's voting power.

Firstly, simple square root calculations would only decrease the relative power of large votes without accounting for the diversity and quantity of voters involved. The strength of Quadratic Voting, similar to Quadratic Funding, is that it **prioritizes the number of individual voters**, meaning that collective decision-making is bolstered and smaller votes gain relatively more weight.

Secondly, by using a quadratic formula rather than a simple square root, our implementation ensures that the **cost of influence increases significantly** the more votes a voter applies to a single decision. This deters an over-concentration of power and incentivizes participants to vote more thoughtfully, spreading their votes across multiple options.

Lastly, Quadratic Voting's strategic voting considerations align better with real-world preferences. People typically have varying degrees of preference for different options. Quadratic Voting, unlike the square root method, encourages voters to express these differences. Voters with strong preferences for specific choices are allowed to **vote multiple times** for these options but at an increasing personal cost.

Overall, our Quadratic Voting system, borrowing principles from Quadratic Funding, balances influence in decision-making and promotes wider participation and diversity of opinion, which simple square root calculations of voting power cannot achieve.

#### **Let's have a look at an example:**

There are 11 voters and three choices, A, B, and C:

* John with 100 SMS tokens
* Bob with 98 SMS tokens
* 9 Marias with 3 SMS tokens each

\-> John allocates all his 95 tokens to A and 5 tokens to B&#x20;

\-> Bob allocates half his 90 tokens to B and 8 tokens to C&#x20;

\-> All 9 Marias allocate their 3 tokens to C

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

3. As a last step, we **match these percentages with the total voting power** of 225 SMS:&#x20;

* A: 16.44% of 225 = **37 SMS**
* B: 24.87% of 225 = **56 SMS**
* C: 58.69% of 225 = **132 SMS**

{% hint style="info" %}
All in all, you don't have to understand each step of the calculation, yet it should give you an idea of how John with 100 SMS tokens was not able to push through his choice despite having the majority of Voting Power in the group as Quadratic Funding model emphasizes the **number of individual contributors** rather than the amount contributed.
{% endhint %}

{% hint style="danger" %}
This Voting System may encourage the whales to create multiple wallets and split their holdings among them. Therefore it's important to also implement a mechanism providing Sybil Resistance. \
\
**Read more** [**here**](broken-reference)**!**
{% endhint %}

**Pros**: Dilutes the whales' voting power in favor of smaller holders. Individuals will matter more than the amount of tokens. \
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
