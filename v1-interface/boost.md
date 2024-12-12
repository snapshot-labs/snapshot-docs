---
description: >-
  Boost is a powerful way to incentivize voting on proposals by rewarding active
  participation or specific actions.
---

# Boost

{% hint style="warning" %}
Be aware that we are currently in the beta testing phase, and the contracts have not yet been audited. This means there's an increased risk of undiscovered bugs. Participate at your own risk and only commit tokens that you can afford to have locked or potentially at risk.
{% endhint %}

### How does it work?

Creating a boost is a straightforward process, here's what happens when you set up a boost:

1. You decide on the number of tokens you wish to commit as a reward and define the [distribution criteria](boost.md#distribution-types).
2. Upon creation, your boost becomes visible to all voters on the proposal page, complete with its criteria, so voters know what incentives are in play.
3. As the creator of the boost, you will receive an NFT from the Boost contract after setting up the boost. This NFT represents your ownership and is essentially your claim ticket for retrieving any unclaimed tokens once the claiming period ends. The retrieval of remaining tokens can be done directly from the proposal page.
4. After the voting on the proposal voting period ends, the claiming period is initiated. This period lasts for two weeks, during which voters can claim their rewards. The length of this period is enforced by us to give voters enough time to claim their rewards.

### Distribution types

When setting up a boost, you have the flexibility to choose how rewards are distributed to voters. Two of the primary distribution types are "Lottery" and "Weighted".

#### Lottery

The lottery system randomly selects winners, where the chances to win are based on voting power. You can set the number of winners who will share the tokens equally, and to level the playing field, implement a cap on voting power. This cap means that beyond a certain point, additional voting power doesn't increase one's chances in the lottery, giving everyone a more fair shot at the reward.

{% hint style="info" %}
The randomness generator we use is the \`ChaCha20Rng\` randomness generator, fed with a specific seed. This seed is the sha256 hash of the RANDAO reveal of the finalized epoch corresponding to the end timestamp of the proposal.
{% endhint %}

#### Weighted

This method allows you to reward voters proportionally to their voting power. You can also set a maximum reward limit per voter to ensure a more equitable distribution and prevent any single voter from receiving a disproportionately large share of the rewards. This can help maintain balance and fairness in the incentive system, especially in spaces where voting power varies significantly between members.

### Benefits of Boost

Boosting has a twofold benefit: increasing participation and allowing for strategic incentivization.

#### Increasing participation

By boosting a proposal, you directly contribute to the governance process, encouraging others to take part in important decisions. Your influence can lead to higher voter turnout and a more robust decision-making process.

#### Strategic incentivization

Boosting allows you to incentivize voting in a way that aligns with your interests. This strategic layer adds depth to the voting process, as participants can receive additional rewards by voting a certain way.

{% hint style="info" %}
If strategic incentivization is not be in line with your space's goals it can be disabled by an admin at space level.
{% endhint %}

### Fee structure

Our platform incorporates a dual-fee system designed to sustain the ecosystem and prevent misuse. While both fees are currently set to zero during our closed beta, they are structured as follows:

#### Boost creation fee

A fixed fee in ETH can be added for Boost creation. Currently, this fee is set to 0 ETH.

#### Token fee

The protocol includes a fee mechanism that can be configured as a percentage of the reward tokens. This fee is paid using the same ERC-20 token committed as the reward and is designed to support the platform’s sustainability. Currently, the token fee is set to 0%. If the fee is enabled in the future, it will be clearly displayed in the interface during the Boost creation process.

### FAQs

<details>

<summary><strong>Can I cancel my boost and retrieve my tokens early?</strong></summary>

No, once a boost is created, the tokens are locked until the end of the claiming period.

</details>

<details>

<summary><strong>What happens if the proposal I boosted doesn't pass?</strong></summary>

The boost still fulfills its purpose by incentivizing voting and participation, regardless of the proposal's outcome.

</details>

<details>

<summary><strong>Are there any additional rewards for creating a boost?</strong></summary>

There are currently no direct rewards for boost creators, but it might help increase your reputation score in the future.

</details>

<details>

<summary><strong>How is the effectiveness of a boost measured?</strong></summary>

Effectiveness can be gauged by the increase in participation on the proposals you've boosted compared to similar proposals without a boost.

</details>

<details>

<summary><strong>What safeguards are in place to prevent abuse of the boosting system?</strong></summary>

We're actively monitoring the use of boosts and will iterate on the rules and mechanisms to prevent any form of abuse as we learn from the beta phase. There are some potential risks with [Strategic incentivization](boost.md), so you might want to disable this feature in your space settings.

</details>
