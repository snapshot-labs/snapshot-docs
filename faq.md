---
description: Frequently asked questions.
---

# FAQs

## :wave: Getting started

<details>

<summary><strong>What is Snapshot?</strong></summary>

Snapshot is an **off-chain voting platform** that allows DAOs, DeFi protocols, or NFT communities to vote easily and **without gas fees**.

The tool allows high customization of the voting process to cater to the diverse needs of the users and organizations. Customization includes different aspects like calculation of the users' voting power, selection of the voting mechanism, proposal and vote validation, and many more.

</details>

<details>

<summary><strong>What does "snapshot" mean?</strong></summary>

In cryptocurrency, a snapshot is a record of the state of the blockchain at a particular block height. It means that you can for example track the holdings of a specific wallet back to a specific point in time. Snapshot, the voting platform, is using snapshots to validate if voters met the voting criteria at the moment of proposal creation. If a voter acquired required tokens after the proposal has been created, these newly acquired tokens would not be used for calculation of their voting power.

</details>

<details>

<summary><strong>Is Snapshot free to use?</strong></summary>

Yes. To create a space, you have to own an ENS domain and perform one transaction on-chain. Voting or proposing is completely free.

</details>

<details>

<summary><strong>Do I need to create a user account?</strong></summary>

No. Snapshot uses the universal web3 login - you need to have a wallet account like Metamask or Coinbase to connect to Snapshot.

</details>

<details>

<summary><strong>What is a space?</strong></summary>

You can think of a space as an organization's **account** on Snapshot which can be viewed by anyone visiting the platform. It serves as a hub for all proposals related to the organization and a source of information for the users. It’s also where users will vote on proposals in their community.

</details>

<details>

<summary><strong>What is a proposal?</strong></summary>

Proposals are key elements of the voting system. It presents a change suggestion related to a specific organization and enables eligible users to cast their vote.

</details>

<details>

<summary><strong>How can I vote?</strong></summary>

You need to connect to Snapshot with your wallet and fulfil the requirements defined by the voting strategies used by a specific space. For example, you might be required to hold a specific amount of the organization’s token. You can see the voting strategies directly on a proposal’s page in the **Information** section:

![](<.gitbook/assets/image (17) (2).png>)

If you don’t understand why your voting power is `0` or how the strategies work in detail, we recommend reaching out to the organization directly. In most cases you don’t have the voting power because you did not hold the required tokens at the time of proposal creation. Tokens which were acquired after the proposal has been create are not taken into account for the voting power calculation.

If you are eligible to vote, you can cast your vote directly from the proposal’s page. Once you select the choice(s) and confirm your vote, a new window will pop up and open your wallet extension in the browser. You will be then asked to sign a message which doesn’t create any gas fees (voting is free of charge) or affect your holdings. Signing the message is the last step of casting a vote. That’s it!

</details>

<details>

<summary><strong>Is voting on Snapshot safe?</strong></summary>

Yes. The message you sign in your wallet to cast the vote doesn’t affect your holdings or web3 identity. There are some spaces which are flagged with a warning badge if we suspect them to be fake but you don’t need to worry if you have cast a vote on their proposal. There is no risk to your funds associated with signing a Snapshot vote. You can read more about the badges in our documentation: [badges-and-warnings.md](user-guides/spaces/badges-and-warnings.md "mention")

</details>

<details>

<summary><strong>I can’t vote, what should I do?</strong></summary>

There might be multiple reasons for that. Most usually you didn’t have the required tokens in you wallet at the time of proposal creation. Have a look at [this discussion ](https://github.com/snapshot-labs/snapshot/discussions/767)to explore other potential reasons.

</details>

<details>

<summary><strong>Is Snapshot open source?</strong></summary>

Yes. All our repositories can be found at [https://github.com/snapshot-labs/](https://github.com/snapshot-labs/).

</details>

<details>

<summary><strong>How can I get in touch?</strong></summary>

If you have an issue with your space, a proposal or voting, make sure to first read the FAQ and use a search bar in our documentation: [https://docs.snapshot.org](https://docs.snapshot.org).

If it doesn’t answer your question or you would like to get in touch with regard to another topic, you can reach us in our [Discord](https://discord.snapshot.org) server and send a message in appropriate channel (i.e. [#general](https://discord.com/channels/707079246388133940/728646188252921956)) or create a new thread on the [#helpdesk](https://discord.com/channels/707079246388133940/1019725253519351838) forum.

</details>



## 👤 I'm a Snapshot user

<details>

<summary><strong>I have an issue, where should I report it?</strong></summary>

Before you report it make sure to browse through this FAQ, our documentation or the Discord server. There is a high chance that the issue has already been discussed before. If not, create a new thread on the [helpdesk forum](https://discord.com/channels/707079246388133940/1019725253519351838) with the following details:

* Clear title describing your issue
* Tags which are related to the problem
* Detailed description of the issue: what action were you trying to perform (i.e. casting a vote), what error did you get
* Screenshots - provide the screenshots of the error you are getting
* URLs - applicable urls, i.e. proposal or space url

</details>

<details>

<summary><strong>I get "Oops, something went wrong!” what should I do?</strong></summary>

We recommend to wait for around 10 minutes and try again. If the error persist, open the console panel (right click with your mouse and click `Inspect` and open the `Console` tab):

![](<.gitbook/assets/image (23).png>)

Make a screenshot of the panel and post a message on the [helpdesk forum on Discord](https://discord.com/channels/707079246388133940/1019725253519351838) with the following details:

* Topic: clear on context when you got the error - Cannot cast a vote - Oops, something went wrong
* What were you attempting to do? (i.e. vote on a proposal, create a proposal)
* Did you wait for some time before trying again?
* Paste the screenshot from the console panel.

</details>

### Voting

<details>

<summary><strong>I delegated my voting power but would like to take it back. How can I do it?</strong></summary>

You can remove your delegations by going to[https://demo.snapshot.org/#/delegate](https://demo.snapshot.org/#/delegate) and clicking the ❌ for the delegations you wish to remove.

![](<.gitbook/assets/image (22).png>)

Moreover, if you want to override your delegate’s vote on a proposal using [the delegation strategy](https://snapshot.org/#/strategy/delegation) you can simply cast your own vote and it will override the delegate’s vote. If the delegation happened on-chain, then head to the delegation portal of the project you’re looking for and redelegate there.

</details>

<details>

<summary><strong>Can I explain the reason for my vote somewhere?</strong></summary>

Yes, apart from the proposals using shielded voting.

You can add a short explanation when casting a vote:

![](<.gitbook/assets/image (34).png>)

</details>

<details>

<summary><strong>I get “Your voting power could not be calculated due to misconfigured strategy or unresponsive RPC node”. What should I do?</strong></summary>

This issue is related to either space settings or the failure of the external infrastructure that Snapshot relies on. We recommend to wait 15 minutes before trying again. If the error persists, please post a message in the [Misconfigured node](https://discord.com/channels/707079246388133940/1070376451070767124/1070376451070767124) thread on helpdesk forum on Discord with the following details:

* URL of the proposal you were trying to vote on
* The error message you received (in this case: “Your voting power could not be calculated due to misconfigured strategy or unresponsive RPC node”)
* Did you wait for 15 minutes before trying to cast the vote again

</details>

<details>

<summary>How can I export the complete voting to excel?</summary>

Go to the proposals page and click the download icon to get a CSV file. You can open it directly in excel or import it in the Google Sheets.

![](<.gitbook/assets/image (32).png>)

</details>

<details>

<summary>Can I vote with a Safe/Multisig?</summary>

Yes. You can find more details in our documentation here: [gnosis-safe.md](user-guides/gnosis-safe.md "mention")

</details>

<details>

<summary>There is a proposal that's open until tomorrow and I have a new token that was minted today, after the proposal’s creation. Can that token be used to vote?</summary>

No. Snapshot calculates the voting power on the basis of proposal creation time. If the token has not been stored in the wallet before the proposal was created it will not be taken into account.

</details>

<details>

<summary>I get “Oops, failed to check voting power”. What should I do?</summary>

This issue is related to either space settings or the failure of the external infrastructure that Snapshot relies on. We recommend to wait 15 minutes before trying again. If the error persists, please post a message in the [thread on helpdesk forum](https://discord.com/channels/707079246388133940/1070378969238601868/1070378969238601868) on Discord with the following details:

* URL of the proposal you were trying to vote on
* The error message you received (in this case: “Oops, failed to check voting power”)
* Did you wait for 15 minutes before trying to cast the vote again

</details>

<details>

<summary><strong>Can I vote on any proposal?</strong></summary>

No. Your eligibility to vote depends on the voting strategies defined by the space and usually requires holding the organization’s token. Some spaces allow anyone to vote, however this is a rare case.&#x20;

You can read more about the voting strategies in our documentation: [what-is-a-strategy.md](user-guides/strategies/what-is-a-strategy.md "mention")

</details>

<details>

<summary>Can I change my vote?</summary>

Yes, you can change your vote as long as the voting period is still active. Simply cast a new vote on the same proposal, and it will overwrite your previous vote.

</details>

### Proposals

<details>

<summary><strong>Can I create a proposal?</strong></summary>

It depends on the space settings. Spaces can set up a validation strategy which defines who is eligible to create a proposal, for example you need to hold at least 1ETH in your wallet in order to do so. Moreover, spaces can specify a list of users who can create proposals by listing their wallet addresses in the space settings. You can read more about [space settings](https://docs.snapshot.org/spaces/settings)  and [proposal validation](https://docs.snapshot.org/strategies/what-is-a-strategy-1).

</details>

<details>

<summary>What happens if a proposal doesn't reach quorum?</summary>

If a proposal does not reach the required quorum, it is considered as not passed. However, the outcome of a proposal depends on the governance rules of the specific project. Some projects might still consider the proposal for further discussion, while others might require resubmission with modifications.

</details>

### Space settings&#x20;

<details>

<summary>It is possible to create a space with a multi-sig account?</summary>

Yes. In order to do so navigate to [https://app.safe.global](https://app.safe.global) and select Snapshot in the `Apps` tab. Your multi-sig address will connect to Snapshot and allow you to create spaces, proposals and vote.

</details>

<details>

<summary>I lost access to my ENS domain which was used to register a space on Snapshot. What should I do?</summary>

If you are still a controller of the space you can apply to delete your space or migrate the current space to another one with different ENS. Have a look at our documentation for more details: [delete-a-space.md](user-guides/spaces/delete-a-space.md "mention")

</details>

<details>

<summary>How can I differentiate settings for proposals and voting?</summary>

You can use sub-spaces on Snapshot. This solution allows you to link multiple spaces and set different settings for each of them depending on your needs. Have a look at our documentation to learn more: [sub-spaces.md](user-guides/spaces/sub-spaces.md "mention")

</details>

<details>

<summary>Can I change the name of my space?</summary>

Yes. You can do it in the space settings.&#x20;

Do not confuse it with changing the `ID` or the ENS domain for your space. To do that, you need to migrate the space. You can read more about changing the ENS domain in our documentation: [delete-a-space.md](user-guides/spaces/delete-a-space.md "mention")

</details>

<details>

<summary>How can I verify my space?</summary>

There is a list of requirements you have to meet. Have a look at our documentation to learn more: [get-verified.md](user-guides/spaces/get-verified.md "mention")

</details>

<details>

<summary>How long does it take to verify a space?</summary>

The process can take up to 72 hours.

</details>

<details>

<summary>I made a mistake with my space settings and I want to cancel existing votes. How can I do it?</summary>

You cannot invalidate existing votes. However you can delete the proposal.

If you are an admin of the space or proposal’s creator you can delete the current proposal by clicking `Delete` on the proposal’s page:

![](<.gitbook/assets/image (25).png>)

Then change the space settings and make sure to persist the changes.

Once the settings have been updated you can recreate the proposal from scratch.

</details>

<details>

<summary>Can I customize the appearance of my Snapshot space?</summary>

Yes, you can customize the appearance of your Snapshot space to some extent by setting a custom skin, which allows you to change the colors of your space. This customization feature is available for spaces using the custom domains setting.

</details>

### Voting strategies

<details>

<summary>What is a strategy?</summary>

Voting strategy is a set of conditions used to calculate user's voting power. Strategies enable Snapshot to calculate the final result of voting on a given proposal. You can read more about them in our documentation: [what-is-a-strategy.md](user-guides/strategies/what-is-a-strategy.md "mention")

</details>

<details>

<summary>I want to test a strategy, how can I do it?</summary>

You can use the playground on Snapshot available from the strategy’s page:

![](<.gitbook/assets/image (31).png>)

</details>

<details>

<summary>How to limit voting to only those users who own a specific amount of the token(s)?</summary>

You need to setup a basic voting validation which allows you to select a specific strategy and define the minimum threshold required for the user to vote. Have a look at our documentation here to learn more: [what-is-a-strategy-1.md](user-guides/strategies/what-is-a-strategy-1.md "mention")

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

You can use sub-spaces on Snapshot. This solution allows you to link different spaces and set different settings for each of them depending on your needs. Have a look at our documentation to learn more: [sub-spaces.md](user-guides/spaces/sub-spaces.md "mention")

</details>

<details>

<summary>I want to give one vote per one wallet to the voters of my space, regardless of their wallets’ balance. Which strategy should I use? </summary>

You can use the [ticket](https://snapshot.org/#/strategy/ticket) strategy.

</details>

<details>

<summary>How can I give 1 voting power to all voters holding a specific token regardless of its amount?</summary>

It's a two step process - you have to define a [validation strategy](user-guides/strategies/what-is-a-strategy-1.md) and a [voting strategy](faq.md#voting-strategies) for your space.\
\
**1. Voting validation** \
In order to allow users to participate in voting, setup a `Basic` voting validation in the space settings. You can find it in the voting section in space settings:\
\
![](<.gitbook/assets/image (1).png>)\
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
![](<.gitbook/assets/image (5).png>)

</details>

<details>

<summary>I am not a developer, can someone work on my strategy for money? </summary>

Yes. You can create an issue on [https://github.com/snapshot-labs/snapshot-strategies/issues](https://github.com/snapshot-labs/snapshot-strategies/issues) and then post in on the [#contributor](https://discord.com/channels/707079246388133940/865557228702662667) channel on Discord.

\
Snapshot is not reponsible for the agreement between you and the contributors.

</details>

## 🧑🏻‍💻 I'm a developer

<details>

<summary>Which networks are currently supported for voting with Gnosis Safe? </summary>

You can find the networks’ IDs here: [https://github.com/snapshot-labs/snapshot-relayer/blob/master/src/check.ts#L9](https://github.com/snapshot-labs/snapshot-relayer/blob/master/src/check.ts#L9)

</details>

<details>

<summary>Do we need to deploy an ENS contract on our custom network to be able to support Snapshot? </summary>

No, it’s not needed.

</details>

<details>

<summary>I think I found a vulnerability on Snapshot. Do you have a bug bounty?</summary>

Yes, we do. Please create report on the respective repository as showed below:

![](<.gitbook/assets/image (33).png>)

</details>

<details>

<summary>Is it possible to test Snapshot without creating ENS on mainnet?</summary>

Yes. You can use the [https://demo.snapshot.org](https://demo.snapshot.org) with an ENS domain on Goerli Testnet.

</details>

<details>

<summary>How does Snapshot use IPFS?</summary>

We use IPFS to pin the receipts of the votes. You can have a more detailed look at the [IPFS article](https://blog.ipfs.tech/2022-08-25-snapshot-ipfs-case-study/).

</details>

<details>

<summary>How to add a webhook? </summary>

Have a look at our documentation: [webhooks.md](tools/webhooks.md "mention")

</details>

### Snaphot.js&#x20;

<details>

<summary>I tried to submit a proposal with <code>snapshot.js</code>, but I get a “Wrong proposal format” error. What should I do?</summary>

There is a high chance that something is missing in the proposal’s payload. Make sure you are following the proposal schema defined here → [https://github.com/snapshot-labs/snapshot.js/blob/master/src/schemas/proposal.json](https://github.com/snapshot-labs/snapshot.js/blob/master/src/schemas/proposal.json)

</details>

<details>

<summary>I tried to submit a vote with <code>snapshot.js</code>, but I get the “Wrong vote format” error. What should I do?</summary>

Make sure that you’re following the vote schema defined here → [https://github.com/snapshot-labs/snapshot.js/blob/master/src/schemas/vote.json](https://github.com/snapshot-labs/snapshot.js/blob/master/src/schemas/vote.json).

A common mistake is using a wrong type (string instead of object) or extending a limit of a value (i.e. `reason` ).

</details>

<details>

<summary>Is there an alternative to <code>snapshot.js</code> in python?</summary>

No. If you are interested in building it, reach out to the team on the [#contributor](https://discord.com/channels/707079246388133940/865557228702662667) channel!

</details>

<details>

<summary>How to use <code>snapshot.js</code> to create a space or update space settings?</summary>

Have a look at our documentation here: [#create-or-edit-a-space](tools/snapshot.js.md#create-or-edit-a-space "mention")

</details>

### Adding a network

<details>

<summary>How can I add our network to Snapshot?</summary>

Follow our documentation to learn all the steps to add a new network to Snapshot: [#add-a-new-network](developer-guides/networks.md#add-a-new-network "mention")

</details>

<details>

<summary>How can I check if the RPC node is a Full Archive Node?</summary>

You can send a request to the node and try to fetch the genesis block:

```
$ curl -H "content-type: application/json" -X POST --data '{"id":0,"jsonrpc":"2.0","method":"eth_getBalance","params":["<CONTRACT_HASH>","0x1"]}' <RPC_URL>
```

If you get a correct response without any errors, the Node is a Full Archive.

</details>

### Creating voting strategies

<details>

<summary>How to use our staking contract for voting? </summary>

You can browse through the existing staking strategies →[https://snapshot.org/#/?type=strategies\&q=stake](https://snapshot.org/#/?type=strategies\&q=stake).

If none of them work for you, have a look at the options below.

* In order to use the staking contract it has to have a `balanceOf` method which allows reading the balance of the staked tokens. You can use the[https://snapshot.org/#/strategy/erc20-balance-of](https://snapshot.org/#/strategy/erc20-balance-of) strategy with it.
* If your contract has a method getting the balance named differently, you can also use the[https://snapshot.org/#/strategy/contract-call](https://snapshot.org/#/strategy/contract-call) strategy.

</details>

<details>

<summary>How long will it take to merge my PR?</summary>

It usually takes around 72 hours so please have some patience. Once the PR is merged, you will also have to wait for a new release of the repository which can take another couple of days.

</details>

<details>

<summary>Is it possible to support delegation on our network?</summary>

Yes. If it’s not supported yet you can create a custom voting strategy to enable delegation on your network. You can see an example here →[https://snapshot.org/#/strategy/orbs-network-delegation](https://snapshot.org/#/strategy/orbs-network-delegation)



To learn more have a look at our documentation: [create-1.md](developer-guides/create-a-strategy/create-1.md "mention")

</details>

<details>

<summary>I get <code>0</code> voting power in the delegation strategy playground but I can vote on real proposals.</summary>

Most probably you are missing the `delegationSpace` parameter. Make sure to provide the ENS domain of the space you are testing.

</details>

<details>

<summary>How to use our token from our network for voting?</summary>

If it doesn’t exist yet, you can create a new voting strategy. Have a look at our documentation to learn more: [create-1.md](developer-guides/create-a-strategy/create-1.md "mention")

</details>



Still can't find an answer? Have a look at our [Github discussions](https://github.com/snapshot-labs/snapshot/discussions/categories/q-a) or follow this question:[#i-have-an-issue-where-should-i-report-it](faq.md#i-have-an-issue-where-should-i-report-it "mention")
