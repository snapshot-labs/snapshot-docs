# 👋 Getting started

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

![](<../.gitbook/assets/image (34).png>)

If you don’t understand why your voting power is `0` or how the strategies work in detail, we recommend reaching out to the organization directly. In most cases you don’t have the voting power because you did not hold the required tokens at the time of proposal creation. Tokens which were acquired after the proposal has been create are not taken into account for the voting power calculation.

If you are eligible to vote, you can cast your vote directly from the proposal’s page. Once you select the choice(s) and confirm your vote, a new window will pop up and open your wallet extension in the browser. You will be then asked to sign a message which doesn’t create any gas fees (voting is free of charge) or affect your holdings. Signing the message is the last step of casting a vote. That’s it!

</details>

<details>

<summary><strong>Is voting on Snapshot safe?</strong></summary>

Yes. The message you sign in your wallet to cast the vote doesn’t affect your holdings or web3 identity. There are some spaces which are flagged with a warning badge if we suspect them to be fake but you don’t need to worry if you have cast a vote on their proposal. There is no risk to your funds associated with signing a Snapshot vote. You can read more about the badges in our documentation: [badges-and-warnings.md](../user-guides/spaces/badges-and-warnings.md "mention")

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

If it doesn’t answer your question or you would like to get in touch with regard to another topic, you can reach us in our [Discord](https://discord.snapshot.org) server and send a message in appropriate channel (i.e. [#general](https://discord.com/channels/707079246388133940/728646188252921956)) or contact our support on [Help Center](https://help.snapshot.org/en/)

</details>
