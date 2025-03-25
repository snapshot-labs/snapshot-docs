---
description: Learn how you can use Snapshot with a Gnosis Safe Multi-sig wallet.
---

# Using Safe multi-sig

You can use a Gnosis Safe to vote, create a proposal or setup a space on Snapshot.&#x20;

{% hint style="warning" %}
Your Safe has to be on the same network as the Space is. Head to Space settings, **Strategies** tab to check the Space's network.
{% endhint %}

### Gnosis Safe interface

{% hint style="info" %}
**Spaces can be created and updated** only by Ethereum Mainnet accounts.\


Voting and proposals related actions are supported by Ethereum Mainnet, Optimism Mainnet, Arbitrum Mainnet, Polygon Mainnet, BSC and Goerli Testnet.
{% endhint %}

To use your multi-sig wallet to interact with Snapshot you can login to Snapshot from Gnosis Safe UI by adding [https://snapshot.org](https://snapshot.org) as a Safe app. When you try an action like vote, it will create a pending transaction in your Safe transactions queue. This transaction must be confirmed by the Safe signers within **72 hours.** Once the transaction is confirmed the vote will be sent and will appear on the proposal.

{% hint style="info" %}
By default, the confirmation modal has to stay open until all Safe signers confirm. \
\
If you prefer to close the modal, you need to enable on chain signatures. Follow the steps from [#asynchronous-signing](using-safe-multi-sig.md#asynchronous-signing "mention") to change your Safe settings.
{% endhint %}

{% embed url="https://www.loom.com/share/31e22ddf57b84fbc9882d9d87b4dded4" %}

### Asynchronous signing

If you'd like to enable asynchronous signing for all Safe's signers and not have to keep the modal open, you have to enable on-chain signatures in the Safe settings.\


1. Go to Safe Settings -> Safe Apps.
2. Enable `Always use on-chain signatures`

<figure><img src="../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>

That's all :tada: Signers can now sign even if you you close the confirmation modal.

