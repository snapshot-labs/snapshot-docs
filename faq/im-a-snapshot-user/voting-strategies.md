# ✨ Voting strategies

<details>

<summary>What is a strategy?</summary>

Voting strategy is a set of conditions used to calculate user's voting power. Strategies enable Snapshot to calculate the final result of voting on a given proposal. You can read more about them in our documentation: [voting-strategies.md](../../user-guides/strategies/voting-strategies.md "mention")

</details>

<details>

<summary>I want to test a strategy, how can I do it?</summary>

You can use the playground on Snapshot available from the strategy’s page:

![](<../../.gitbook/assets/image (31).png>)

</details>

<details>

<summary>How to limit voting to only those users who own a specific amount of the token(s)?</summary>

You need to setup a basic voting validation which allows you to select a specific strategy and define the minimum threshold required for the user to vote. Have a look at our documentation here to learn more: [validation-strategies.md](../../user-guides/strategies/validation-strategies.md "mention")

</details>

<details>

<summary>Why is my voting power equal to <code>0</code>? </summary>

There might be multiple reasons for that. Most usually your voting power is equal to 0 as you didn’t have the required tokens in you wallet at the time of proposal creation. Have a look at [this discussion](https://github.com/snapshot-labs/snapshot/discussions/767) to explore other potential reasons.

</details>

<details>

<summary>Why is my voting power reduced? I’m a delegate. </summary>

If the proposal’s space is using the [delegation strategy](https://snapshot.org/#/strategy/delegation) and the address which delegated its voting power to you casts a vote on the specific proposal, your total voting power is reduced by the delegation which you received from the other address.

To give an example (using the `delegation` strategy):

* B has voting power of 20 of its own.
* A has voting power of 10 and delegates it to B.
* B has now a voting power equal to 30.
* If A does not vote, B’s voting power is 30.
* If A does vote, B’s voting power is 20. (30 reduced by 10)

</details>

<details>

<summary>I'm looking to set up our Snapshot space with 3 different voting strategies for 3 types of proposals. How can I do it? </summary>

You can use sub-spaces on Snapshot. This solution allows you to link different spaces and set different settings for each of them depending on your needs. Have a look at our documentation to learn more: [sub-spaces.md](../../user-guides/spaces/sub-spaces.md "mention")

</details>

<details>

<summary>I want to give one vote per one wallet to the voters of my space, regardless of their wallets’ balance. Which strategy should I use? </summary>

You can use the [ticket](https://snapshot.org/#/strategy/ticket) strategy.

</details>

<details>

<summary>How can I give 1 voting power to all voters holding a specific token regardless of its amount?</summary>

It's a two step process - you have to define a [validation strategy](../../user-guides/strategies/validation-strategies.md) and a [voting strategy](voting-strategies.md#voting-strategies) for your space.\
\
**1. Voting validation** \
In order to allow users to participate in voting, setup a `Basic` voting validation in the space settings. You can find it in the voting section in space settings:\
\
![](<../../.gitbook/assets/image (65).png>)\
\
When defining the voting validation parameters, you have the option to specify the `strategies` for the tokens and the `minScore` required for voters to be eligible to vote:

Here is an example of the basic strategy setup for voters holding DAI tokens:

```
{
  "minScore": 1, # define the minimum required amount of token
  "strategies": [
   {
      "name": "erc20-balance-of",
      "params": { # define the specific token details
        "address": "0x6b175474e89094c44da98b954eedeac495271d0f",
        "symbol": "DAI",
        "decimals": 18
      }
  ]
}
```

**2. Voting strategy**&#x20;

Use the [Ticket](https://snapshot.org/#/strategy/ticket) strategy to give voting power equal to `1` to any user eligible to vote - users that passed the voting validation described in step 1.\
![](<../../.gitbook/assets/image (73).png>)

</details>

<details>

<summary>I am not a developer, can someone work on my strategy for money? </summary>

Yes. You can create an issue on [https://github.com/snapshot-labs/snapshot-strategies/issues](https://github.com/snapshot-labs/snapshot-strategies/issues) and then post in on the [#developers](https://discord.com/channels/707079246388133940/747050056422785055) channel on Discord.

\
Snapshot is not reponsible for the agreement between you and the contributors.

</details>
