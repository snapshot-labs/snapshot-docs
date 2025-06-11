---
description: Learn how you can use Snapshot with a Gnosis Safe Multi-sig wallet.
---

# Using Safe multi-sig

You can use a Gnosis Safe to vote, create a proposal or setup a space on Snapshot.&#x20;

{% hint style="warning" %}
Your Safe has to be on the same network as the Space is. Head to Space settings, **Strategies** tab to check the Space's network.
{% endhint %}

{% hint style="info" %}
**Spaces can be created and updated** only by Ethereum Mainnet accounts.

Voting and proposals are accepted from Space's network only.
{% endhint %}

## Connecting your Safe

To connect your Safe to Snapshot

1. Go to your Safe wallet like `https://app.safe.global/apps/open?safe=<NETWORK>:<SAFE_ADDRESS>`
2. Go to the **Apps** tab.
3. Search for Snapshot and click on it.
4. You should now see the Snapshot interface connected to your Safe wallet.

{% embed url="https://www.loom.com/share/f02b6ec7a95e44a88f9a4ebba281e002" %}

## Signing with your Safe

There are two ways to sign with your Safe multi-sig wallet on Snapshot:

1. **Synchronous signing (offchain)** - you keep the confirmation modal open until all Safe signers confirm the transaction.

2. **Asynchronous signing (onchain)** - you can close the confirmation modal and the transaction will be created in your Safe transactions queue. The Safe signers can confirm it later.

For more information, refer to the [Gnosis Safe documentation](https://help.safe.global/en/articles/40783-what-are-signed-messages).

### Synchronous signing

By default, the first signer who is signing a message will have to keep the confirmation modal open until all other signers confirm the message.

This happens offchain and does not create a transaction in your Safe transactions queue. but in messages tab of your Safe. Other signers need to confirm the message in their Safe interface.

### Asynchronous signing

If you'd like to enable asynchronous signing for all Safe's signers and not have to keep the modal open, you have to enable on-chain signatures in the Safe settings.\

1. Go to Safe Settings -> Safe Apps.
2. Enable `Always use on-chain signatures`

<figure><img src="../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>

That's all :tada: Signers can now sign even if you you close the confirmation modal.

It will create a pending transaction in your Safe transactions queue. This transaction must be confirmed by the Safe signers within **144 hours.**
