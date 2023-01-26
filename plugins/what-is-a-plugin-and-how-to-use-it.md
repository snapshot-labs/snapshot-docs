---
description: Learn what plugins are and how to use them.
---

# What is a plugin and how to use it?

Plugin is an extension which enriches Snapshot by additional functionalities without changing the core of Snapshot's logic. The possibilities are many, from plugins which reward users with an NFT when they cast a vote, through adding a comment box for voters to explain their choice, to enabling on-chain execution of Gnosis Safe transactions.

You can browse through all plugins by heading to [https://snapshot.org](https://snapshot.org) and selecting the **Plugins** filter in the search bar:

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

## Add a plugin to your space&#x20;

You can extend your space's functionality by adding plugin(s) to it. They will be applied to all proposals created after the plugin has been added.

1. In order to add a plugin head to your space settings by clicking **Settings** on your space's page:

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

2\. Scroll down to the **Plugins** section and click **Add plugin**. Select the plugin you want to add in the pop-up window:

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

3\. Configure the plugin according to your needs. \
\
Each plugin requires different setup so before you add it to your space make sure which parameters do you need to provide. As an example, the Gnosis SafeSnap plugin requires a `CHAIN_ID` of the network your safe is using and the `realityAddress` . Check out the [gnosis-safe.md](../gnosis-safe.md "mention") setup steps if you want to learn more about this specific plugin.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

4\. Click **Add** and don't forget to **Save** your new settings.&#x20;

5\. Well done, you have added a new plugin to your space! :tada:

{% hint style="info" %}
The newly added plugin will affect only **proposals created after** the settings have been updated.
{% endhint %}
