# Overview

Snapshot X's main contract is the **Space** contract. Proposals are created, votes are cast, and all of the proposal state is stored here. Beyond this however, the majority of the protocol functionality has been abstracted out of the Space contract. &#x20;

These abstractions consist of:&#x20;

* [Who can create a proposal](proposal-validations.md).&#x20;
* [How users are authenticated](authenticators.md).&#x20;
* [How the voting power is determined](voting-strategies.md). &#x20;
* [How a proposal passes and how it's being executed](execution-strategies.md).

This approach allows a far higher degree of modularity and customisability than what would be possible if all of this logic was handled directly by the Space contract itself.&#x20;

Creating a space on Snapshot X is **like creating a new character in a game**. First you need to select an armour to protect your character, then you need to decide on a weapon (spear, sword, bow). Finally, you need to choose a mount for your character to get him to travel from town to town faster.

With that analogy in mind, think about the **Space** contract like the character, and the [**Authenticators**](authenticators.md), [**Proposal validation strategies**](proposal-validations.md), [**Voting strategies**](voting-strategies.md)**,** and [**Execution strategies**](execution-strategies.md) like the different add-ons you need to decide on. We refer to them collectively as **Snapshot X Modules**.&#x20;

Let's go over those briefly:

**Authenticators** \
Determine how the participants can be _authenticated_ to create a proposal or cast a vote. In general this will be some kind of signature or transaction caller verification.&#x20;

**Proposal validation strategies**\
Determine how an author is validated to create a proposal. A common approach is checking that the author exceeds a certain threshold proposition power calculated through a set of strategies. &#x20;

**Voting strategies**\
Determine how the voting power is computed. Voting strategies are custom contracts that allow you to determine how you compute the voting power of each participant in the vote. Arbitrary logic can be implemented here to create complex and expressive governance mechanisms. The most common way of voting is voting with your tokens (1 token = 1 voting power, so if you have 100 tokens you get a total voting power of 100). This is a voting strategy. But you could imagine other voting strategies: for example, only give voting power to the owners of a specific NFT. Or maybe use a quadratic model, where users only get the square root of their token balance (to minimise the power of whales).&#x20;

**Execution strategies**\
Have two key roles:&#x20;

1\) Determine the _status_ of a proposal at any time during its lifetime.

2\) Determine _what should happen_ once a proposal passes.&#x20;

This latter role will generally consist of executing a set of transactions linked to the proposal. The strategy can control which contracts are authorised to execute the transactions or alternatively execute them directly itself.

\
This modularity allows anyone to extend the basic protocol to suit their requirements. We provide a set of pre-built and audited modules but **we invite you to write your own!**

## So what does the flow look like?

The full usage flow looks like this:

1. A DAO deploys a **Space** contract and defines space settings along with a set of authenticators, voting strategies, and a proposal validation strategy.&#x20;
2. A user can create a **proposal** in the **Space** via a whitelisted authenticator. The proposal validation strategy is queried to check that the user is eligible to create the proposal. \
   To create a proposal, the proposer has to specify an execution strategy contract along with an execution payload that will contain the encoded set of transactions inside the proposal.&#x20;
3. Users can vote on the proposal by authenticating through one of the whitelisted authenticator contracts.
4. Once the voting period has ended, anyone can execute the proposal permissionlessly. This will forward the execution payload to the execution strategy and execute the transactions included.

The below diagram showcases an example of how the contracts that make up Snapshot X fit together along with various actions users can take to create proposals, vote, execute proposals, and update settings.

{% embed url="https://whimsical.com/snapshot-x-evm-on-chain-architecture-M3d8bU1V2Z7r6kbVUM9g2w" %}

{% hint style="info" %}
If you are planning to integrate Snapshot X into your own product, head to [SX.js](broken-reference) section to learn about our SDK.
{% endhint %}
