---
description: Learn what a proposal is and how to create one.
---

# Proposals

## ​​What is a proposal?&#x20;

Proposal is the key element of the voting system. It presents a change suggestion related to a specific organization and enables eligible users to cast their vote.

Voting power for each user is calculated on the basis of the voting strategies selected in the [space settings](broken-reference).​

Each proposal has the same voting system which provides three choices: **accept**, **reject**, **abstain**.

## Who can create a proposal? <a href="#who-can-create-a-proposal" id="who-can-create-a-proposal"></a>

Users who:

* authenticate themselves via Authenticators[^1] whitelisted by the space,&#x20;
* and are eligible according to the [Proposal validation strategy](#user-content-fn-2)[^2] selected by the space.

## Create a proposal <a href="#create-a-proposal" id="create-a-proposal"></a>

### 1. Open space settings.

Head to the space which you wish to create your proposal for.

Make sure the connected wallet is **where you hold the tokens relevant** to the specific space.&#x20;

### 2. Click the New proposal icon

Click the new proposal icon in the top right corner:\


<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### 3. Provide proposal details

Provide the necessary details - title, description and discussion link if there is one.

### 4. Choose the execution strategy

Select the [Execution strategy](#user-content-fn-3)[^3] you would like to use:\


<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### 5. Specify transaction details

Define what should happen if the proposal passes by choosing one of the execution options:

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

A modal will open with the **transaction details** to fill in:\


<figure><img src="../../.gitbook/assets/Screenshot 2023-04-26 at 11.44.20.png" alt=""><figcaption></figcaption></figure>

### 6. Publish your proposal

Click `Publish`​ and authenticate yourself via your wallet. Depending on the [space settings](broken-reference) you will have to sign a gasless Ethereum message and/or sign a transaction to confirm your action.

{% hint style="info" %}
When you create a proposal by default the **timestamp** will be populated with the latest block synced from our node. The voting power of each user will be calculated for the **state of the blockchain at this specific timestamp**. \
\
It means that if user acquires required tokens **after** the proposal has been created, they will not be taken into account for their voting power calculation.​
{% endhint %}

### 7. Give it a minute..

Wait for the transaction to succeed. You can see it's pending in the top right corner, just next to your avatar:\


<figure><img src="../../.gitbook/assets/Screenshot 2023-04-26 at 11.57.20.png" alt=""><figcaption></figcaption></figure>



Once the icon with the pending transaction disappears, you can reload the page to view your proposal.

And that's it! You have created a new proposal :tada:

### Executing proposals <a href="#proposals-limitations" id="proposals-limitations"></a>

Once the proposal has reached a quorum and passed, anyone can execute the transactions specified for it by clicking the **Execute transactions** button:

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-20 at 11.20.56.png" alt=""><figcaption></figcaption></figure>

[^1]: Authenticators define how users can authenticate themselves to take specific actions. You can learn more about them [here](../protocol/authenticators.md).

[^2]: A proposal validation strategy defines the minimum Voting power required to create a new proposal. Learn more [here](../protocol/proposal-validations.md).

[^3]: Execution strategies determine the status of the proposal and are responsible for execution of the proposal payload once it has passed. If you want to learn more, check [here](../protocol/execution-strategies.md).
