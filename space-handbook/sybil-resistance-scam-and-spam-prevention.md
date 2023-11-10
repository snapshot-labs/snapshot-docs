---
description: >-
  How to avoid scams, spam and make sure that your proposal authors and voters
  are genuine humans? How can you take into account users' on-chain reputation?
  Read on!
---

# Sybil resistance, scam & spam prevention

> A **Sybil attack** is a type of attack on a computer [network service](https://en.wikipedia.org/wiki/Network\_service) in which an attacker subverts the service's reputation system by creating a large number of [pseudonymous](https://en.wikipedia.org/wiki/Pseudonymity) identities and uses them to gain a disproportionately large influence.\
>
>
> _source:_ [_https://en.wikipedia.org/wiki/Sybil\_attack_](https://en.wikipedia.org/wiki/Sybil\_attack)

In the crypto world, attacks, hacks, and scams are unfortunately all too common. Phishing links can be found everywhere - on Twitter, in seemingly harmless blog posts, and in personal emails. We’ve not been immune to them either! As a popular tool for decentralized decision-making, [Snapshot.org](http://snapshot.org/) is an attractive target for scammers looking to manipulate governance proposals for their own gain.

## How to make your Space more Sybil resistant?

There are multiple ways which can help you minimize the risk of scams, bots and spam behaviors within your space. We will look into:

* [Space roles](sybil-resistance-scam-and-spam-prevention.md#1.-space-roles)
* [Validation Strategies](sybil-resistance-scam-and-spam-prevention.md#2.-validation-strategies) (use for Proposal Creation and Voting)
* [Voting Strategies ](sybil-resistance-scam-and-spam-prevention.md#3.-voting-strategies)(use for Voting Validation)

## 1. Space roles

Let’s first recap what are the different permissions of the [roles](../user-guides/spaces/space-roles.md) defined in the **Members** tab of the Space settings:

* **Controller** - in full control of the space, the only role able to change the Controller of the space.
* **Admin** - able to modify the space settings (apart from the list of Admins), manage the space’s proposals and create proposals.
* **Moderator** - able to manage the space’s proposals and create proposals.
* **Author** - able to create proposals without having to go through proposal validation.

### Moderators

Even though we provide several automated mechanisms to minimise the risk of harmful proposals it is still important to have to ability to review the created proposals by an **actual person**.

The Moderator role enables just that - without having the access to space settings moderators **can hide proposals**. It is a great way to have more organization members involved in keeping the governance safe without requiring Admins to be available at all times.

#### Discord Bot

A great addition to the Moderators is a **notification system** which will inform you and your community about newly created proposals. If your organization uses Discord, you can easily activate our Discord Bot on your server.

To do so, invite the bot with [this link](https://discord.com/oauth2/authorize?client\_id=892847850780762122\&permissions=83968\&scope=bot).

Then type `/` to see the commands (require administrator role):

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Voilà! Now you and your Moderators can keep an eye on the notifications and react much quicker when a scam proposal has hit your space.

### Authors

It is also possible to whitelist accounts which will be allowed to create new proposals regardless of the chosen Validation Strategy (more on the strategies in the next section).

Once added as **Authors** in the **Members** tab in the space settings they will surpass the validation process and will be able to create new proposals in the space.

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

#### Authors only mode

If you wish to limit proposal creators to Admins, Moderators and Authors only, you can do so by enabling the **Authors only** setting in the **Proposal** tab in the space settings. Make sure to give the Author role to the users you trust!

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

## 2. Validation Strategies

In technical terms a [Validation Strategy](https://docs.snapshot.org/user-guides/strategies/what-is-a-strategy-1) is a JavaScript function that returns a boolean (`true` or `false`) for the connected account to define if someone is eligible to create a new proposal or cast a vote.

> **Each space can use one Proposal and one Voting Validation for all of its proposals at a time**.

Validation strategy can check both for monetary and non-financial assets of the user like POAPs, Gitcoin Passport stamps.

{% hint style="info" %}
All spaces are now **required to use Proposal Validation** in order to minimize the risk of malicious proposals.
{% endhint %}

### Basic Validation

The[ Basic Validation Strategy](../user-guides/strategies/validation-strategies.md#validation-strategy-example-basic) allows you to specify multiple **Voting Strategies** to determine if a user is eligible to create a proposal.

> [Voting Strategy](https://docs.snapshot.org/user-guides/strategies/what-is-a-strategy) is a set of conditions used to calculate user's voting power. Strategies enable Snapshot to calculate the final result of voting on a given proposal.

When setting the Validation Strategy up it’s important to keep in mind that it is **meant to make it difficult for users outside of your community to post scam proposals**.

Therefore make sure to use a **high threshold**, for example $100 worth of your organization’s token. A good idea would be to check the holdings of previous proposal creators, both legitimate and scammers, to assess a reasonable value.

> In case the threshold you’ve set is too high for some of your community members, don’t forget that you can always add the trusted addresses as Authors, thanks to which they will surpass the Proposal Validation stage.

Below you can see an example of the **Basic Proposal Validation** using Voting Strategies set for the space:

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

If you want to set up a more complex validation, you can use custom strategies as shown on the screenshot below:

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

### Gitcoin Passport Validation

While Basic Validation focuses on the monetary assets, [this validation](../user-guides/strategies/validation-strategies.md#validation-strategy-example-gitcoin-passport) allows you to set requirements protecting your space against Sybil attacks by checking the [Gitcoin Passport](https://passport.gitcoin.co/) stamps which serve as validation for user’s identity and online reputation.

You can select individual or multiple stamps that matter for your space. You can also decide if they need to meet all of these criteria or only one. The more criteria you select, the more sybil resistant your space is.

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

## 3. Voting Strategies

### [membership](https://snapshot.org/#/strategy/membership)

Useful when combined with Quadratic Voting, which provides a certain level of Sybil resistance.

The strategy combines any arbitrary Voting Strategy defining a membership with any Voting Strategy calculating the Voting Power of a user. In the idea **one can only vote if he passes the membership strategy**, the membership here can be an identity symbol like possessing a [UID](https://etherscan.io/address/0xba0439088dc1e75F58e0A7C107627942C15cbb41) or a [PUNK](https://etherscan.io/token/0xb47e3cd837ddf8e4c57f05d70ab865de6e193bbb) (with an `erc721` strategy) or any other custom verification strategy based on on-chain behavior.

The membership portion is binary. If the membership strategy returns any number > 0 for an address, then user is considered a member and their Voting Power will be the result of the `votingPowerStrategy`.&#x20;

Otherwise voting power for that address will be 0.&#x20;

**Strategy setup:**

```
{
    "membershipStrategy": {
      "name": "erc721",
        "params": {
          "address": "0xb47e3cd837ddf8e4c57f05d70ab865de6e193bbb"
        }
    },
    "votingPowerStrategy": {
      "name": "erc20-balance-of",
        "params": {
          "address": "0x6b175474e89094c44da98b954eedeac495271d0f",
          "symbol": "DAI",
          "decimals": 18,
        }
    },
    "symbol": "DAI"
  }
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/membership?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiQkFMIiwiYWRkcmVzcyI6IjB4YmExMDAwMDA2MjVhMzc1NDQyMzk3OGE2MGM5MzE3YzU4YTQyNGUzRCIsImRlY2ltYWxzIjoxOH0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHgzMjk1ZGY0MWEyZjI4OGRhMDM4MThhZTMyNTY1ZTE1OTlmMWIyZWVlIiwiMHgyMDcyMzBFMDZlMTRkMWZhOTRlNzAzZjQ3ODRGODE5NjY3NDcyMjQ3IiwiMHgwMDU1NTk2NjUyMWRmOWVkYmNhOWI4YTQ5N2FkODAzMWNmMzNmNzJhIl19" %}

### [whitelist](https://snapshot.org/#/strategy/whitelist)

Assuming the wallet address has been verified to prove its identity by the Space admins the simplest way to implement is to use whitelist strategy which only allows addresses passed into the param to vote on proposals, which is 1 vote 1 address.

{% hint style="info" %}
The wallet address can also be its corresponding **ENS domain.**
{% endhint %}

{% hint style="success" %}
To assign arbitrary votes to a specific address, see [whitelist weighted](https://snapshot.org/#/strategy/whitelist-weighted).
{% endhint %}

**Strategy setup:**

```
{
  "symbol": "POINT",
  "addresses": [
    "0xa478c2975ab1ea89e8196811f51a7b7ade33eb11",
    "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7"
  ]
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/whitelist?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiQkFMIiwiYWRkcmVzcyI6IjB4YmExMDAwMDA2MjVhMzc1NDQyMzk3OGE2MGM5MzE3YzU4YTQyNGUzRCIsImRlY2ltYWxzIjoxOH0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHhhNDc4YzI5NzVhYjFlYTg5ZTgxOTY4MTFmNTFhN2I3YWRlMzNlYjExIiwiMHhlRjgzMDVFMTQwYWM1MjAyMjVEQWYwNTBlMmY3MWQ1ZkJjQzU0M2U3IiwiMHgxRTFBNTFFMjVmMjgxNjMzNWNBNDM2RDY1ZTlBZjc2OTRCRTIzMmFkIl19" %}
