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

### Distribution Types

When setting up a boost, you have the flexibility to choose how rewards are distributed to voters. Two of the primary distribution types are "Lottery" and "Weighted".

#### Lottery

The lottery system randomly selects winners, where the chances to win are based on voting power. You can set the number of winners who will share the tokens equally, and to level the playing field, implement a cap on voting power. This cap means that beyond a certain point, additional voting power doesn't increase one's chances in the lottery, giving everyone a more fair shot at the reward.

{% hint style="info" %}
The randomness generator we use is the \`ChaCha20Rng\` randomness generator, fed with a specific seed. This seed is the sha256 hash of the RANDAO reveal of the finalized epoch corresponding to the end timestamp of the proposal.
{% endhint %}

#### Weighted

This method allows you to reward voters proportionally to their voting power. You can also set a maximum reward limit per voter to ensure a more equitable distribution and prevent any single voter from receiving a disproportionately large share of the rewards. This can help maintain balance and fairness in the incentive system, especially in spaces where voting power varies significantly between members.

### Benefits of Boosting

Boosting has a twofold benefit: increasing participation and allowing for strategic incentivization.

#### Increasing Participation

By boosting a proposal, you directly contribute to the governance process, encouraging others to take part in important decisions. Your influence can lead to higher voter turnout and a more robust decision-making process.

#### Strategic Incentivization

Boosting allows you to incentivize voting in a way that aligns with your interests. This strategic layer adds depth to the voting process, as participants can receive additional rewards by voting a certain way.

{% hint style="info" %}
If strategic incentivization is not be in line with your space's goals it can be disabled by an admin at space level.
{% endhint %}

### Fee Structure

Our platform incorporates a dual-fee system designed to sustain the ecosystem and prevent misuse. While both fees are currently set to zero during our closed beta, they are structured as follows:

#### ETH Fee

A nominal fee of 0.01 ETH will be implemented as a spam prevention measure. This fee also helps cover any network fees incurred by the platform during the operation.

#### Token Fee

{% hint style="warning" %}
We have set both the ETH fee and the Token fee to zero for our closed beta testing phase.
{% endhint %}

In addition to the ETH fee, a token fee of 3% will be taken from the deposited tokens. This fee is essential for the platform's revenue, allowing us to continue providing quality services, innovating our offerings, and supporting the community. The token fee is calculated based on the total token amount committed to the boost at the time of creation.

Both fees are designed to be reasonable and ensure the longevity and integrity of the platform. Participants will always have full visibility of any applicable fees before finalizing their boost creations.

### FAQs

{% content-ref url="../faq/im-a-snapshot-user/boost.md" %}
[boost.md](../faq/im-a-snapshot-user/boost.md)
{% endcontent-ref %}
