---
description: Learn how to create a new space for your organization.
---

# Create a space

Head to the [Create space page](https://snapshot.box/#/create) and follow the below steps:

## 1. Organization's details

Provide the profile information like `name`, `description`, social links or handles and `treasury`.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-26 at 10.19.09.png" alt=""><figcaption></figcaption></figure>

In order to set your Treasury select the network first.

{% hint style="info" %}
**Treasury** is the address of your organisation's main account.
{% endhint %}

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-03 at 13.58.47.png" alt=""><figcaption></figcaption></figure>

## 2. Select network

Choose the network for your organisation. At the moment Snapshot X works with Ethereum.

ℹ️ _Starknet implementation is coming soon._

## 3. Voting strategies

Voting Strategies calculate the **Voting Power** of each user.

{% hint style="info" %}
If you are not familiar with what a Voting Strategy is head to [Broken link](broken-reference "mention") to learn more.
{% endhint %}

Select a Voting Strategy from the list of available options and provide the required details.

For example for the **Delegated Compound Token** you have to provide the token contract address, its decimals and the symbol:

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-26 at 10.21.13.png" alt=""><figcaption></figcaption></figure>

## 4. Authenticators

Choose how users will be authenticated in order to create a proposal or cast a vote.

{% hint style="info" %}
If you are not familiar with what Authenticators are head to [Broken link](broken-reference "mention")to learn more.
{% endhint %}

The two authenticators provided by Snapshot X are:

#### [Ethereum signature](broken-reference)

It will authenticate a user based on a message signed by an Ethereum private key.

#### [Ethereum transaction](broken-reference)

Users have to submit a transaction on Ethereum. Authentication is proving that the sender's address is valid.

## 5. Proposal validation

Proposal Validation is setting **requirements** that user needs to meet in order to **create a new proposal.**

{% hint style="info" %}
If you are not familiar with what a Proposal Validation is head to [Broken link](broken-reference "mention") to learn more.
{% endhint %}

Define the minimum Voting Power required to create a new proposal.

**⚠️ We highly recommend setting a high threshold to avoid scam proposals. ⚠️**

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-03 at 14.05.50.png" alt=""><figcaption></figcaption></figure>

Once you have defined the required Voting Power, you can then select the Voting Strategies which will be used to calculate the voting power of proposal creators and assess the eligibility to create a new one:

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-03 at 14.11.17.png" alt=""><figcaption></figcaption></figure>

## 6. Execution

Execution Strategies have two key roles:

1. determining **the status** of a proposal at any time,
2. and **executing the payload** of a proposal if it has been accepted.

{% hint style="info" %}
If you are not familiar with what Execution Strategies are head to [Broken link](broken-reference "mention") to learn more.
{% endhint %}

When selecting the execution strategy you have to provide a **quorum** - minimum number of votes required for a proposal to pass.

### Execution strategies

Currently Snapshot X provides two Execution Strategies:

#### Avatar

-> ideal solution for treasuries on [Safe](https://safe.global/)

-> executes transactions on an [Avatar contract](https://github.com/gnosis/zodiac/blob/master/contracts/interfaces/IAvatar.sol)

-> uses simple quorum

{% hint style="info" %}
Avatar contract is any contract which implements the `IAvatar`interface.\
**Safe** is an example of an Avatar contract.
{% endhint %}

{% hint style="warning" %}
To set the Avatar Execution Strategy up fully you have to enable it on your Safe account after you have created your space.\
\
**Follow this guide to complete the setup:**\
[Broken link](broken-reference "mention")
{% endhint %}

#### Timelock

-> adds additional **security layer** to review or cancel transactions before they get executed

-> executes transactions after a delay specified in **seconds**

-> uses simple quorum

{% hint style="info" %}
When a proposal with this strategy is executed, the proposal transactions are queued in the Timelock for `timelockDelay` seconds before they can be executed.
{% endhint %}

### 7. Voting

Customize the setup for voting which will affect **all proposals** in your space:

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-26 at 10.46.38.png" alt=""><figcaption></figcaption></figure>

* **Voting delay** - The delay between when a proposal is created, and when the voting starts. A value of 0 means that as soon as the proposal is created anyone can vote while a value of 3600 means that voting will start 3600 seconds after the proposal is created.
* **Minimum voting duration** - The minimum duration of the voting period. It is **impossible to execute a proposal before** **this period** has elapsed.
* **Maximum voting duration** - The maximum duration of the voting period, it is **impossible to cast a vote after this period** has passed. The **`minimum voting duration`** must be less than or equal to this value.

{% hint style="info" %}
We highly recommend implementing a Voting Delay to allow more time to review proposal's content and identify malicious proposals before voting starts.
{% endhint %}

### 7. Controller

Space controller is a user that has a **full control over the space settings.**

The address can differ from your own, you can for example set a multisig account as the controller.

### 8. Sign transaction(s)

Click **Create** and sign transaction(s) in your wallet. You will have to sign multiple transactions, each for individual contracts to be deployed:

* Space contract
* Execution strategy contracts - each space has its execution strategy deployed as an individual contract

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

And that's it! 🎉
