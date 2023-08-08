---
description: >-
  Which Voting strategy to choose to enable enable users to vote on behalf of
  their delegators?
---

# Delegation

{% hint style="info" %}
Delegation enables you to delegate your voting power to another wallet. Unlike other actions in Snapshot, the delegation itself is an **on-chain behavior**, requiring some gas fees to execute a delegation transaction.\
\
Within this page we will be using two terms:\
\- _delegator_ - user who delegated their Voting power to another address\
\- _delegate_ - the user who was delegated the Voting power and can vote on behalf of others
{% endhint %}

## How can users delegate their Voting power?

Before we jump straight into the Voting strategies setup, let's first understand how users can delegate their Voting power to others through Snapshot.

\<UPDATE FOR NEW DELEGATION UI>

## Voting strategies

In order to take the delegated Voting power into account, your space **has to use one of the delegation** Voting strategies.&#x20;

{% hint style="warning" %}
If the delegation-based Voting strategies are not set for your space, even if users have delegated their VP or are delegates themselves, their Voting power will be calculated only on the basis of their own assets.\
\
**This means  👉  Delegation will not work.**
{% endhint %}

\
In Snapshot, based on whether the delegated power can be taken back by the delegators when they vote, there are **two main** delegation strategies:

* `with-delegation` -  the delegator cannot vote, only the delegate can participate in voting
* `delegation` - allows the delegator to vote despite having delegated their Voting power

Let's have a look at both in detail:

### [with-delegation](https://snapshot.org/#/strategy/with-delegation)

This strategy is a combination of **delegation** + **own Voting power** (if not delegated to anyone), moreover, it **prevents the delegators from taking back their delegated VP**.&#x20;

By using this strategy, one can no longer vote if he delegated to another one, and the delegatee's voting power will be his own VP + delegated VP.

{% hint style="warning" %}
Delegators[^1] **cannot vote on proposals** if this strategy is used in the Space and if they have delegated their VP to another address (for the current space or all spaces). \
\
If delegators wish to participate in voting themselves, they have to revoke their delegation for the current space or all spaces **before the creation of the proposal**.
{% endhint %}

The sub-strategies are used to define the source of own VP and delegation.

**Strategy setup**

{% hint style="info" %}
Note that you can pass the **`delegationNetwork`**as the optional parameter so that the strategy can **read delegation from one network** and **Voting power from other networks**.

This is useful when the space has multiple strategies across chains and wants to enable delegation for all the relevant tokens.&#x20;

The space can specify the same **`delegationNetwork`** in all strategies so users will only need to delegate once in one network instead of delegating respectively on each chain to have all vp delegated
{% endhint %}

```json
{
  "symbol": "POH (delegated)",
  "delegationSpace": "poh.eth",
  "delegationNetwork": "1",
  "strategies": [
    {
      "name": "erc20-balance-of",
      "params": {
        "address": "0x1dAD862095d40d43c2109370121cf087632874dB",
        "decimals": 0
      }
    }
  ]
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/with-delegation?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiUE9IIChkZWxlZ2F0ZWQpIiwiZGVsZWdhdGlvblNwYWNlIjoicG9oLmV0aCIsInN0cmF0ZWdpZXMiOlt7Im5hbWUiOiJlcmMyMC1iYWxhbmNlLW9mIiwicGFyYW1zIjp7ImFkZHJlc3MiOiIweDFkQUQ4NjIwOTVkNDBkNDNjMjEwOTM3MDEyMWNmMDg3NjMyODc0ZEIiLCJkZWNpbWFscyI6MH19XX0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHgzYzEzZjJCNTZBRjYxNGFDNjM4MTI2NUVjQjNCNjE5YkEyNkNDNjQxIiwiMHgwNDhmZWU3YzMyNzlhMjRhZjA3OTBiNmIwMDJkZWQ0MmJlMDIxZDJiIiwiMHgxMzlhOTAzMmE0NmMzYWZlMzQ1NmViNWYwYTM1MTgzYjVmMTg5Y2FlIl19" %}

### [delegation](https://snapshot.org/#/strategy/delegation)

This strategy returns the **delegated Voting power only.**&#x20;

{% hint style="info" %}
In order to count delegate's full Voting power including their own holdings and the delegation, you need to set up regular strategies for the space, like for example `erc20-balance-of` or `balance-of-woth-thresholds`.
{% endhint %}

Now, what's the deal with both delegate and delegator casting a vote?

**In the `delegation` strategy, if A delegates to B and both of them vote, then the delegated voting power is not calculated. Only the vote of A will be calculated.**&#x20;

**The vote of B will be counted if A does not vote.**

It can include a list of sub-strategies (`erc20-...`, `erc1155-...`, `whitelist`, etc) to calculate the user's Voting power based on the delegation.

**Strategy setup**

The below example shows that the space allows YFI balance as the delegated voting power in `yam.eth` space.

{% hint style="info" %}
The parameter **`delegationSpace`** is optional in space settings. By default it takes delegations of current space.&#x20;

However, **if you're testing delegation in the playground**, you have to specify the space ENS name to let it know from which space you're fetching one's delegation.
{% endhint %}

```json
{
  "symbol": "YFI (delegated)",
  "delegationSpace": "yam.eth",
  "strategies": [
    {
      "name": "erc20-balance-of",
      "params": {
        "address": "0xBa37B002AbaFDd8E89a1995dA52740bbC013D992",
        "symbol": "YFI",
        "decimals": 18
      }
    }
  ]
}son
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/delegation?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiUE9IIChkZWxlZ2F0ZWQpIiwic3RyYXRlZ2llcyI6W3sibmFtZSI6ImVyYzIwLWJhbGFuY2Utb2YiLCJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4MWRBRDg2MjA5NWQ0MGQ0M2MyMTA5MzcwMTIxY2YwODc2MzI4NzRkQiIsImRlY2ltYWxzIjowfX1dfSwibmV0d29yayI6IjEiLCJzbmFwc2hvdCI6IiIsImFkZHJlc3NlcyI6WyIweDNjMTNmMkI1NkFGNjE0YUM2MzgxMjY1RWNCM0I2MTliQTI2Q0M2NDEiLCIweDA0OGZlZTdjMzI3OWEyNGFmMDc5MGI2YjAwMmRlZDQyYmUwMjFkMmIiLCIweDEzOWE5MDMyYTQ2YzNhZmUzNDU2ZWI1ZjBhMzUxODNiNWYxODljYWUiXX0." %}

[^1]: By _delegators_ we mean users who have delegated their Voting power to other address, the _delegate._
