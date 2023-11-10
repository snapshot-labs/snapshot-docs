---
description: Learn about the most popular configurations.
---

# Most common

Before we jump into specific use cases, let's have a look at the most common configurations that the majority of spaces use on Snapshot.

## Voting strategy + Proposal validation strategy

The minimum setup required to run your governance on Snapshot consists of:

* selecting at least one Voting strategy
* choosing a Validation strategy for proposal creation

{% hint style="info" %}
To recap what Voting and Validation Strategies are:

:zap: [**Validation strategies**](../user-guides/strategies/validation-strategies.md) are a way to define who is allowed to vote on a proposal or create a new one.&#x20;

:zap: [**Voting strategies**](../user-guides/strategies/voting-strategies.md) calculate how much Voting power each user has.
{% endhint %}

## Most common Voting strategies

### Token based

#### [erc20-balance-of](https://snapshot.org/#/strategy/erc20-balance-of)

{% hint style="info" %}
\#1 Voting strategy on Snapshot used by over 8 thousand Spaces.
{% endhint %}

This strategy returns the balance for a specific ERC20 token that user holds in their wallet.

**Strategy setup:**

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/erc20-balance-of" %}

#### [eth-balance](https://snapshot.org/#/strategy/eth-balance)

This strategy returns the balance of the user's ETH holdings as their Voting power.

**Strategy setup:**

You only need to provide the `ETH` symbol:

```
{
  "symbol": "ETH"
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/eth-balance?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiQkFMIiwiYWRkcmVzcyI6IjB4YmExMDAwMDA2MjVhMzc1NDQyMzk3OGE2MGM5MzE3YzU4YTQyNGUzRCIsImRlY2ltYWxzIjoxOH0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHhhNDc4YzI5NzVhYjFlYTg5ZTgxOTY4MTFmNTFhN2I3YWRlMzNlYjExIiwiMHhlRjgzMDVFMTQwYWM1MjAyMjVEQWYwNTBlMmY3MWQ1ZkJjQzU0M2U3IiwiMHgxRTFBNTFFMjVmMjgxNjMzNWNBNDM2RDY1ZTlBZjc2OTRCRTIzMmFkIiwiMHgxRjcxN0NlOGZmMDc1OTdlZTdjNDA4YjU2MjNkRjQwQWFBZjE3ODdDIiwiMHgxYzdhOTI3NUYyQkQ1YTI2MEE5YzMxMDY5Rjc3ZDUzNDczYjhhZTJlIiwiMHgxZDVFNjVhMDg3ZUJjM2QwM2EyOTQ0MTJFNDZDRTVENjg4Mjk2OWY0IiwiMHgxZjI1NDMzNkU1YzQ2NjM5QTg1MWI5Q2ZDMTY1Njk3MTUwYTZjMzI3IiwiMHgyZWMzRjgwQmVEQTYzRWRlOTZCQTIwMzc1MDMyQ0REM2FBZmIzMDMwIiwiMHg0QWNCY0E2QkUyZjhEMjU0MGJCRjRDQTc3RTQ1ZEEwQTRhMDk1RmEyIiwiMHg0RjNEMzQ4YTZEMDk4MzdBZTc5NjFCMUUwY0VlMmNjMTE4Y2VjNzc3IiwiMHg2RDdmMjNBNTA5RTIxMkJhNzc3M0VDMWIyNTA1ZDFBMTM0ZjU0ZmJlIiwiMHgwN2ExZjZmYzg5MjIzYzVlYkQ0ZTRkZGFFODlBYzk3NjI5ODU2QTBmIiwiMHg4ZDVGMDUyNzBkYTQ3MGUwMTViNjdBYjUwNDJCRGJFMkQyRkVGQjQ4IiwiMHg4ZDA3RDIyNWE3NjliN0FmM0E5MjM0ODFFMUZkRjQ5MTgwZTZBMjY1IiwiMHg4ZjYwNTAxZEU1YjliMDFGOUVBZjEyMTRkYkUxOTI0YUE5N0Y3ZmQwIiwiMHg5QjhlOGREOTE1MTI2MGMyMUNCNkQ3Y2M1OTA2N2NkOERGMzA2RDU4IiwiMHgxN2VhOTJENkZmYkFBMWM3RjZCMTE3YzFFOUQwYzg4QUJkYzhiODRDIiwiMHgzOEMwMDM5MjQ3QTMxRjM5MzliYUU2NWU5NTM2MTIxMjVjQjg4MjY4Il19" %}

#### [erc721](https://snapshot.org/#/strategy/erc721)

{% hint style="info" %}
This strategy is designed for NFT holdings and is similar to [erc20-balance-of](most-common.md#erc20-balance-of).
{% endhint %}

This strategy returns the balance for a specific ERC721 NFT as the user's Voting Power.

**Strategy setup:**

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/erc721" %}

[**eth-with-balance**](https://snapshot.org/#/strategy/eth-with-balance)

**eth-with-balance** in its simplest way to assign **1 vote** to wallets holding **any** balance of ETH.   Regardless of how big the balance is, the VP is always the same and equal to 1 VP. If the wallet doesn't hold any ETH, the VP is 0.

{% hint style="info" %}
This allows you to poll your community without referencing the number of ETH they hold, **each address will have 1VP**.\
\
If you want to use this approach for another token, have a look at the [**erc20-with-balance**](https://snapshot.org/#/strategy/erc20-with-balance) strategy.
{% endhint %}

You can also use this strategy to set a voting threshold by adding an optional parameter `minBalance` and defining the minimum required balance which will give the user the **eligibility to vote** and **1 Voting Power**. The parameter value is set to 0 by default.&#x20;

{% hint style="info" %}
Using a low minimum balance, this strategy can be used as a proxy for "active Ethereum address", based on the assumption that active addresses will always have some ETH to pay the fees.
{% endhint %}

**Strategy setup:**

```
{
  "symbol": "ETH",
  "minBalance": 0.5
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/eth-with-balance?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiQkFMIiwiYWRkcmVzcyI6IjB4YmExMDAwMDA2MjVhMzc1NDQyMzk3OGE2MGM5MzE3YzU4YTQyNGUzRCIsImRlY2ltYWxzIjoxOH0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHhhNDc4YzI5NzVhYjFlYTg5ZTgxOTY4MTFmNTFhN2I3YWRlMzNlYjExIiwiMHhlRjgzMDVFMTQwYWM1MjAyMjVEQWYwNTBlMmY3MWQ1ZkJjQzU0M2U3IiwiMHgxRTFBNTFFMjVmMjgxNjMzNWNBNDM2RDY1ZTlBZjc2OTRCRTIzMmFkIiwiMHgxRjcxN0NlOGZmMDc1OTdlZTdjNDA4YjU2MjNkRjQwQWFBZjE3ODdDIiwiMHgxYzdhOTI3NUYyQkQ1YTI2MEE5YzMxMDY5Rjc3ZDUzNDczYjhhZTJlIiwiMHgxZDVFNjVhMDg3ZUJjM2QwM2EyOTQ0MTJFNDZDRTVENjg4Mjk2OWY0IiwiMHgxZjI1NDMzNkU1YzQ2NjM5QTg1MWI5Q2ZDMTY1Njk3MTUwYTZjMzI3IiwiMHgyZWMzRjgwQmVEQTYzRWRlOTZCQTIwMzc1MDMyQ0REM2FBZmIzMDMwIiwiMHg0QWNCY0E2QkUyZjhEMjU0MGJCRjRDQTc3RTQ1ZEEwQTRhMDk1RmEyIiwiMHg0RjNEMzQ4YTZEMDk4MzdBZTc5NjFCMUUwY0VlMmNjMTE4Y2VjNzc3IiwiMHg2RDdmMjNBNTA5RTIxMkJhNzc3M0VDMWIyNTA1ZDFBMTM0ZjU0ZmJlIiwiMHgwN2ExZjZmYzg5MjIzYzVlYkQ0ZTRkZGFFODlBYzk3NjI5ODU2QTBmIiwiMHg4ZDVGMDUyNzBkYTQ3MGUwMTViNjdBYjUwNDJCRGJFMkQyRkVGQjQ4IiwiMHg4ZDA3RDIyNWE3NjliN0FmM0E5MjM0ODFFMUZkRjQ5MTgwZTZBMjY1IiwiMHg4ZjYwNTAxZEU1YjliMDFGOUVBZjEyMTRkYkUxOTI0YUE5N0Y3ZmQwIiwiMHg5QjhlOGREOTE1MTI2MGMyMUNCNkQ3Y2M1OTA2N2NkOERGMzA2RDU4IiwiMHgxN2VhOTJENkZmYkFBMWM3RjZCMTE3YzFFOUQwYzg4QUJkYzhiODRDIiwiMHgzOEMwMDM5MjQ3QTMxRjM5MzliYUU2NWU5NTM2MTIxMjVjQjg4MjY4Il19" %}

### Other

#### [whitelist](https://snapshot.org/#/strategy/whitelist)

Another very popular strategy that gives you control over who can cast the votes. All you need to do is to provide the addresses which should be eligible to vote, and each will have 1 Voting Power.

{% hint style="info" %}
The wallet address can also be its corresponding **ENS domain.**
{% endhint %}

{% hint style="success" %}
To assign arbitrary votes to a specific address, see [whitelist weighted](https://snapshot.org/#/strategy/whitelist-weighted).
{% endhint %}

{% hint style="danger" %}
Note that if you add other Strategies to your space and users meet the criteria set by those Strategies, the **whitelist** approach will not work anymore. \
\
To be able to combine multiple Voting strategies for whitelisted users, use the [Basic Validation strategy](../user-guides/strategies/validation-strategies.md#validation-strategy-example-basic) in a custom setup with the `whitelist` strategy selected, and a minimum score of 1 VP.&#x20;
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

## Validation strategies

:zap: [**Validation strategies**](../user-guides/strategies/validation-strategies.md) are a way to define who is allowed to vote on a proposal or create a new one.&#x20;

{% hint style="info" %}
All spaces are now **required to use Proposal Validation** in order to minimize the risk of malicious proposals. You can read more about this requirement [here](../user-guides/spaces/settings.md#proposal-validation).
{% endhint %}

You can also configure a Validation strategy for voting. The combination of Voting Strategies and Voting validation allows you to achieve high customization of your governance process. How? Let's go through a couple of possible scenarios:

* You are using several Voting strategies for the Voting Power calculation, and at the same time, you want to require each user to have at least 10 VP to be able to cast a vote. You can then use [Basic Validation](../user-guides/strategies/validation-strategies.md#validation-strategy-example-basic) with a minimum score of 10.
* Only specific users should be able to vote, and their Voting Power should depend on their holdings. You can use [`whitelist`](most-common.md#whitelist) strategy in the custom Basic Validation setup, and any combination of Voting Strategies for the calculation of the individual Voting power.
* Your space is attacked by bots and you want only genuine humans to cast votes. You can use the [Gitcoin Validation](../user-guides/strategies/validation-strategies.md#validation-strategy-example-gitcoin-passport) for Sybil resistance, and select a combination of Voting Strategies for VP calculation.

Let's have a look at the currently available strategies:

### Basic Validation

The[ Basic Validation Strategy](../user-guides/strategies/validation-strategies.md#validation-strategy-example-basic) allows you to specify multiple **Voting strategies** to determine if a user is eligible to create a proposal.

> [Voting Strategy](https://docs.snapshot.org/user-guides/strategies/what-is-a-strategy) is a set of conditions used to calculate user's voting power. Strategies enable Snapshot to calculate the final result of voting on a given proposal.

When setting the Validation strategy up it’s important to keep in mind that it is **meant to make it difficult for users outside of your community to post scam proposals**.

Therefore make sure to use a **high threshold**, for example, $100 worth of your organization’s token. A good idea would be to check the holdings of previous proposal creators, both legitimate and scammers, to assess a reasonable value.

> In case the threshold you’ve set is too high for some of your community members, don’t forget that you can always add the trusted addresses as Authors, thanks to which they will surpass the Proposal Validation stage.

Below you can see an example of the **Basic Proposal Validation** using Voting Strategies set for the space:



<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

If you want to set up a more complex validation, you can use custom strategies as shown in the screenshot below:

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

### Gitcoin Passport Validation

While Basic Validation focuses on the monetary assets, [this validation](../user-guides/strategies/validation-strategies.md#validation-strategy-example-gitcoin-passport) allows you to set requirements protecting your space against Sybil attacks by checking the [Gitcoin Passport](https://passport.gitcoin.co/) stamps which serve as validation for the user’s identity and online reputation.

You can select individual or multiple stamps that matter for your space. You can also decide if they need to meet all of these criteria or only one. The more criteria you select, the more Sybil-resistant your space is.

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

##
