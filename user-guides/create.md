---
description: Learn what a proposal is and how to create one.
---

# Create a proposal

## What is a proposal?

Proposal is the key element of the voting system. It presents a change suggestion related to a specific organization and enables eligible users to cast their vote.

A specific [voting system](../proposals/voting-types.md) (single choice, weighted, quadratic, and others) can be selected individually for each proposal.

Voting power for each user is calculated on the basis of the voting strategies selected in the [space settings](voting-strategies.md).

## Who can create a proposal?

Space [controller](spaces/space-roles.md),[ admins](spaces/space-roles.md), [authors](spaces/space-roles.md), and users who are eligible according to the [proposal validation](validation-strategies.md) strategies defined in the space settings.

{% hint style="danger" %}
**Proposal limit**\
\
Each space has a limit on the number of proposals that can be created daily and monthly. For more details have a look at [#proposals-limitations](create.md#proposals-limitations "mention")
{% endhint %}

## Create a proposal

1. Head to the space which you wish to create your proposal for.
2. Connect with the wallet provider - make sure the connected wallet is **where you hold the tokens relevant** to the specific space.
3.  Click `New proposal` in space sidebar:\\

    <figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>
4.  Fill in the following fields:\
    \- Title\
    \- Description (optional, 10K character limit)\
    \- Discussion link (optional)\\

    <figure><img src="../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>
5.  Select the desired voting system, specify the possible vote options, and define the duration of your proposal. Make sure you allow enough time for users to vote.\\

    <figure><img src="../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>
6. Click `Publish` - and that's it! You can see your proposal in the proposals list on the space page.

## **Snapshot block number**

When you create a proposal by default the **snapshot block number** will be populated with the latest block synced from our node.

{% hint style="warning" %}
The voting power of each user will be calculated for the **state of the blockchain at this specific snapshot**.\
\
It means that if the user acquires required tokens **after** the proposal has been created, they will not be taken into account for their voting power calculation.
{% endhint %}

### Proposals limitations

* There is a character limit of **10,000** for the description of a proposal.
* One address can have a maximum of **10 active proposals at a time**, across multiple spaces.
* Each space has a limit on the number of proposals created daily and monthly:

| Space status                     | Daily proposal limit | Monthly proposal limit |
| -------------------------------- | -------------------- | ---------------------- |
| [Turbo](spaces/turbo-plan.md)    | 40                   | 200                    |
| [Verified](spaces/get-verified/) | 20                   | 100                    |
| Unverified                       | 3                    | 15                     |
| Flagged                          | 1                    | 5                      |

{% hint style="info" %}
Learn more about Space verification and flagging in [badges-and-warnings.md](spaces/badges-and-warnings.md "mention").
{% endhint %}

* You can combine up to **8** [voting strategies](voting-strategies.md). The limit also applies to multi-chain strategies. ([Turbo](spaces/turbo-plan.md) spaces can add up to **10** strategies)
* All testnet spaces will have the same proposal limits as a Verified space
* Can add up to **20** choices on a proposal ([Turbo](spaces/turbo-plan.md) spaces can add up to **1000** choices)
