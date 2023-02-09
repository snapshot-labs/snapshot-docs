---
description: Learn what a voting strategy is and how to set it up.
---

# Voting strategies

## What is a voting strategy?

Voting strategy is a set of conditions used to calculate user's voting power. Strategies enable Snapshot to calculate the final result of voting on a given proposal.

> &#x20;In technical terms a strategy is a JavaScript function that returns a score for a set of addresses.&#x20;

Strategy/-ies are defined in the space settings in [#voting-strategies](../spaces/settings.md#voting-strategies "mention") section. Each space can select from one up to eight voting strategies. The default strategy is `erc20-balance-of` - it calculates the balance of a predefined ERC20 token for each user.

Voting strategies can be used to create a score from on-chain data, the data however does not necessarily need to be monetary. As an example a strategy can calculate how many POAPs or specific NFTs a user owns.

You can browse through 400+ strategies by selecting the **Strategies** filter on the main page of [https://snapshot.org](https://snapshot.org). If you can't find a strategy that fulfills your needs you can create a new one. To learn more about creating custom voting strategies head to [create-1.md](../guides/create-1.md "mention").

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

## How to set up a strategy?

Majority of spaces on Snapshot is using a single strategy however if you need a more complex calculation, you can combine up to 8 strategies. They will be applied to all proposals created for your space (created _after_ the update of the settings) and the voting power will be calculated cumulatively.&#x20;

{% hint style="info" %}
**Multiple voting strategies**\
****If you combine several voting strategies the voting power will be calculated in the following way:\
_total voting power = voting power from strategy A + voting power from strategy B + ..._
{% endhint %}

\
In order to set up a voting strategy head to your space settings and scroll down to **Strategies** section. You should see the below pop-up after clicking **Add strategy** and selecting a strategy from the list:

<figure><img src="../.gitbook/assets/image (4) (3).png" alt=""><figcaption><p>Example of setting up an erc20-balance-of strategy.</p></figcaption></figure>

You will see that there is information that you need to provide in order to make the strategy work, for example the **network** where the token is deployed, its **symbol** and **address** of the token's contract.&#x20;

Each strategy will require a different setup and you can read the full description and see the required parameters in the strategy's page, for example [erc20-balance-of](https://snapshot.org/#/strategy/erc20-balance-of). You can find each strategy's details through using the search bar and **Strategies** filter.

## Testing a voting strategy

Before you add the strategy to your space's settings we highly recommend to test it in the **Playground** in order to avoid any potential issues with the voting process.

{% hint style="danger" %}
If you made a mistake in your space settings and votes have already been cast **it is not possible to revert them.** \
The best solution would be to (1) delete the proposal, (2) update the settings with correct **** strategies **** and (3) recreate the proposal from scratch after the settings have been updated.
{% endhint %}

You can access it from the strategy's detail page by clicking the **Playground** on the right-hand side:

<figure><img src="../.gitbook/assets/image (6) (3).png" alt=""><figcaption></figcaption></figure>

Your browser will load a Playground page where you can test the custom setup for the chosen strategy. As you can see on the below screenshot you can set the required parameters and provide a list of addresses which in this case are or are not holding a the `PUNK` ERC721 token.&#x20;

<figure><img src="../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>

If everything is set up correctly you should see the calculated voting power for each address after clicking the :arrow\_forward: button:

<figure><img src="../.gitbook/assets/image (27) (1).png" alt=""><figcaption></figcaption></figure>
