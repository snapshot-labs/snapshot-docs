---
description: Learn more about the different ways you can vote on Snapshot
---

# Voting systems

{% hint style="info" %}
Snapshot supports a number of different voting types and we plan to support many more in the future. If you would like to request a new voting type, please open a feature request here [https://features.snapshot.org/feature-requests](https://features.snapshot.org/feature-requests)
{% endhint %}

Voting systems represent the method used to calculate the results of a vote on the basis of the voting power. While voting strategies calculate voting power, voting systems calculate the results of votes.

Depending on your proposal, different voting systems also allow users to:&#x20;

* Choose one option only (single choice voting)&#x20;
* Spread their votes over multiple options (weighted voting)&#x20;
* Weigh the results based on individual addresses as well as voting power (quadratic voting)&#x20;
* Approve a certain number of options (approval voting)&#x20;
* Rank the different choices in their order of preference (ranked-choice voting)&#x20;
* Abstain from voting while still participating in quorum (basic voting)

Let's look more in depth at each voting type:

### Single choice voting

Each voter may select only one choice. The results will reflect these votes in terms of percentages. Ideal for choosing one option from many.\
\
Pros: Most simple and common voting system.\
Cons: Voters can only pick one option.

[Try it for yourself !](https://snapshot.org/#/pistachiodao.eth/proposal/0x02c3fcd64e86157d07c88e5a715ac08f57655917f8bfd5be30a99092136511ec)&#x20;

### Approval voting

Each voter may select ("approve") any number of choices, each selected choice will receive equal voting power.

Pros: Ask approval for several decisions in a single proposal.\
Cons: There is no way to manifest _how much_ you support each choice. It’s a simple yes or no.

[Try it for yourself !](https://snapshot.org/#/pistachiodao.eth/proposal/0x08c3bd2960700525770a1d634f8599ba967e55fcc05b6c1649d984d88253769d)

### Quadratic voting

Each voter may spread voting power across any number of choices. The results are calculated quadratically, so the number of individual voters matters more than the voting power contributed. For more information on quadratic voting, head here: [https://en.wikipedia.org/wiki/Quadratic\_voting](https://en.wikipedia.org/wiki/Quadratic\_voting)

Pros: Dilutes the whales voting power in favor of smaller holders. Individuals will matter more than tokens. \
Cons: This voting type needs to be accompanied by a Sybil-resistance mechanism that prevents whales from simply splitting funds across different wallets.

[Try it for yourself !](https://snapshot.org/#/pistachiodao.eth/proposal/0x21f64875abbca71762a980efae43ab62b546d54f19a208d0e61a5d7cee571a35)

### Ranked choice voting (Instant Runoff Voting)

Each voter may rank the different choices in any order. Votes are initially counted for each voter's number one choice. If a candidate has more than half of the vote based on number one choices, that choice wins. If not, then the choice with the fewest number one votes is eliminated. Voters who had chosen the defeated choice as number one now have their number two choice counted as number one choice. The process continues over multiple rounds until a choice has more than half the votes.

The calculation of the results stops when one choice has more than 50% of the votes.\
Some options will show up as if they had not received any votes because they were eliminated in the ranked-choice voting process.

Pros: Determines the option with the strongest support and reduces wasted votes. \
Cons: Complex to understand. Will only determine one winner, doesn’t work well to select 2 or more winning options.

[Try it for yourself !](https://snapshot.org/#/pistachiodao.eth/proposal/0x5003da0f03e718b461e53fe10a998b60172e2e108472153282fcef781c300f23)

### Weighted voting

Each voter may spread voting power across any number of choices. Their voting power will be divided between their chosen option according to how much weight you attribute each option.

Voters distribute their voting power between any number of options.

Pros: Allows voters to express support for more than one option and specify how much you support each.\
Cons: Slightly complexifies the voting process.

This voting method was first introduced by Float Protocol with [Scattershot](https://github.com/FloatProtocol/scattershot) (a fork of Snapshot).

[Try it for yourself !](https://snapshot.org/#/pistachiodao.eth/proposal/0xf93f1ac80e22cc930b1eef1d20bd34671ccc33b88b04695479c9de364451d77f)

### Basic voting

Each voter can select one of three options: For, Against, Abstain.

While voters can choose the option to abstain, these votes will count towards reaching the necessary quorum for a proposal to pass.

Pros: Easy to interpret and hard to contest results.\
Cons: Limited flexibility of the choices.

[Try it for yourself !](https://snapshot.org/#/pistachiodao.eth/proposal/0x38c654c0f81b63ea1839ec3b221fad6ecba474aa0c4e8b4e8bc957f70100e753)
