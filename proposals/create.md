---
description: Learn how to create a proposal.
---

# Create a proposal

### What is a proposal?&#x20;

TBD

### How to create a proposal

* Go to a project space and tap on the "Connect wallet" button in the top right corner.
* Connect with the wallet provider where you hold relevant tokens and tap on “New proposal.”
* Fill out the Title, Description (optional,) and Discussion (optional) link of your proposal.
* Tap on the “Continue” button and select the desired [voting system](https://docs.snapshot.org/proposals/voting-types) and add your voting options.
* Enter the start date and end date of your proposal to determine the proposal voting period. Make sure you allow enough time for voting.
* Use the default [Snapshot block number](create.md#add-a-snapshot-block-number) or you can change it according to your needs. The block number is the snapshot where the balance of voters will be counted.&#x20;
* Tap on “Publish” and your proposal is created!&#x20;

### **Add a Snapshot block number**

This number is important to lock the state of community members who are able to vote. Note that only the community members who hold relevant amounts of tokens at the time of the creation of the **Snapshot block number** would be able to vote on the proposal. ****&#x20;

When you create a proposal, by default the "snapshot block number" will be populated with the latest block sync from our node. You can use this default number while creating a proposal or just look at [etherscan.io/blocks](https://etherscan.io/blocks) and use the last block number.

Depending on the settings of the space, either everyone holding a sufficient amount of tokens can vote or only members holding a sufficient amount of tokens can submit a proposal.

### Proposals limitations

* There is a character limit of 6400 for the description of a proposal.
* Strategies are limited to 8. You should also respect this limitation when you use the multi-chain strategy.
