---
description: Learn how you can vote with Gnosis Safe Multi-sig wallet.
---

# Vote with Gnosis Safe

You can use a Gnosis Safe to vote, create a proposal or setup a space on Snapshot.&#x20;

### Gnosis Safe interface

To do so you can login to Snapshot from Gnosis Safe UI by adding [https://snapshot.org](https://snapshot.org) as a Safe app. When you will try an action like vote, it will create a pending transaction in your Safe transactions queue. This transaction must be confirmed by the Safe signers within 72 hours. Once the transaction is confirmed the vote will be sent and will appear on the proposal.

### Vote directly on Snapshot

You can also cast your votes directly on[ https://snapshot.org](https://snapshot.org).

Navigate to [https://snapshot.page/#/delegate/](https://snapshot.page/#/delegate/), and connect your Gnosis Safe using the [Safe App for WalletConnect](https://help.gnosis-safe.io/en/articles/4356253-how-to-use-walletconnect-with-the-gnosis-safe-multisig). Then, enter an address of an EOA wallet or ENS name you control or to which you would like to delegate, and click `Confirm.`

After, you will be able to see the EOA wallet address(es) you’ve delegated to from your Gnosis Safe whenever you return to this page. Delegated addresses allow you to use an EOA wallet that represents the governance token holdings in your Gnosis Safe. In order to participate in Snapshot polls through delegation, make sure you’ve connected the wallet to which you’ve delegated.

{% hint style="info" %}
For a delegated address to be effective when signaling on a Snapshot poll, the address has to have been delegated to by the **block number** set on the Snapshot poll.
{% endhint %}

Follow the recording below for a visual guidance:

{% embed url="https://www.loom.com/share/31e22ddf57b84fbc9882d9d87b4dded4" %}



{% hint style="info" %}
Only Ethereum Mainnet, Optimism Mainnet, Arbitrum and Polygon Mainnet are supported at the moment.
{% endhint %}

{% hint style="warning" %}
**Any action** on Snapshot done with a **Gnosis Safe** require a TX that will require **gas fees.**
{% endhint %}
