---
description: Learn more about the different voting schemes on Snapshot.
---

# Voting systems

{% hint style="info" %}
Snapshot supports a number of different voting systems and we plan to support many more in the future. If you would like to request a new voting type, please open a feature request [here](https://features.snapshot.org/feature-requests) :pray:&#x20;
{% endhint %}

## What is a voting system?

Voting system defines how users can cast their votes and how the final result is calculated.

Do not mistake it with the voting strategy though - a [voting strategy](../strategies/what-is-a-strategy.md) is used to calculate the **individual voting power** of a user while the voting system calculates the **outcome of the proposal**.

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

👉 [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x02c3fcd64e86157d07c88e5a715ac08f57655917f8bfd5be30a99092136511ec)****

<figure><img src="../.gitbook/assets/image (8) (2).png" alt=""><figcaption></figcaption></figure>

### Weighted voting

Each user can spread their voting power across any number of choices, from one to all. Their voting power will be divided between their chosen options according to how much weight they attribute to each option by increasing or decreasing the voting power fraction.

**Pros**: Allows voters to express support for more than one option and specify how much they support each of them.\
**Cons**: Requires more time and adds complexity to the voting process.

This voting method was first introduced by Float Protocol with [Scattershot](https://github.com/FloatProtocol/scattershot) (a fork of Snapshot).

****:point\_right: [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0xf93f1ac80e22cc930b1eef1d20bd34671ccc33b88b04695479c9de364451d77f)****

<figure><img src="../.gitbook/assets/image (4) (2).png" alt=""><figcaption></figcaption></figure>

### Approval voting

Each user can select (_approve_) any number of choices, each selected choice will receive equal voting power, i.e. if user selects two choices, each choice will receive the total voting power of the user.

**Pros**: Ask for approval of several decisions in a single proposal.\
**Cons**: There is no way to manifest _how much_ you support each choice. It’s a simple yes or no.

:point\_right: [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x08c3bd2960700525770a1d634f8599ba967e55fcc05b6c1649d984d88253769d)****

<figure><img src="../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

### Quadratic voting

Each user can spread voting power across any number of choices. The results are calculated quadratically, thanks to which the **number of individual voters** matters more than the sum of voting power contributed.&#x20;

For more information on quadratic voting refer to [this article](https://en.wikipedia.org/wiki/Quadratic\_voting).

**Pros**: Dilutes the whales' voting power in favor of smaller holders. Individuals will matter more than the amount of tokens. \
**Cons**: This voting type needs to be accompanied by a [Sybil-resistance mechanism](../strategies/what-is-a-strategy-1.md) that prevents whales from splitting funds across different wallets.&#x20;

:point\_right: [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x21f64875abbca71762a980efae43ab62b546d54f19a208d0e61a5d7cee571a35)****

<figure><img src="../.gitbook/assets/image (6) (3).png" alt=""><figcaption></figcaption></figure>

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

:point\_right: [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x5003da0f03e718b461e53fe10a998b60172e2e108472153282fcef781c300f23)****

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### Basic voting

Each user can select one of three options: `For`, `Against`, `Abstain`.

The votes cast on the `Abstain` choice are counted in calculating if the necessary quorum has been reached for a proposal to pass.

**Pros**: Results are easy to interpret and hard to contest.\
**Cons**: Choices are predefined and cannot be edited.&#x20;

:point\_right: [**Try it yourself!**](https://snapshot.org/#/pistachiodao.eth/proposal/0x38c654c0f81b63ea1839ec3b221fad6ecba474aa0c4e8b4e8bc957f70100e753)****

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
