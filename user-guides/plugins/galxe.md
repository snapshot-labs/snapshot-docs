---
description: Learn what Galxe plugin is and how to add it to your space.
---

# Galxe

[Galxe](https://galxe.com/) is building a protocol that powers on-chain credentials with plug-and-play NFT modules. The permissionless infrastructure allows everyone to create, distribute, and gamify NFTs with customized on-chain data.

With the Galxy plugin users can easily create a campaign and integrate it into [Snapshot.](https://snapshot.org) This solution will incentivize communities to participate in the proposal vote by rewarding them with OATs (On-Chain Achievement Tokens). After users have voted, they can claim an OAT directly from the Project Galaxy Plugin section on the proposal page on Snapshot.

## Setup

### 1. Go to your settings

In order to add a plugin head to your space settings by clicking **Settings** on your space's page:

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

### 2. Create a new proposal

Create a new proposal which you would like to link to the Galxe plugin. You don't need to specify anything related to Galxe yet.

Once the proposal is created, copy the proposal ID from the address bar in your browser as you will need it in the next step.

<figure><img src="../../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>

### 3. Add the plugin

2\. Scroll down to the **Plugins** section and click **Add plugin**. Select the plugin you want to add in the pop-up window:

<figure><img src="../../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

Add the proposal ID and the Galxe Campaign information which you would like to link with the proposal.

<figure><img src="../../.gitbook/assets/image (130).png" alt=""><figcaption></figcaption></figure>

\
Make sure to replace `<Proposal ID>` with your proposal ID which you copied in the previous step.

Then replace the `<Space Name/campaign/Campaign ID>` with the details of your space and campaign.

_Example:_

```json
"oats": {
	"0x554ca2bd7d979e8b72c6ae6415946a7bb470da9f60a9cf931205f083c03632a3": "jokey/campaign/GCixQUUqfE"
}
```

\
If you have multiple proposals that distribute OATs to voters, you can also add multiple `proposalID:campaignInfo` pairs at once in the following format:

```json
{
	"oats": {
		"<proposal ID 1>": "<Space Name>/campaign/<Campaign ID>",
		"<proposal ID 2>": "<Space Name>/campaign/<Campaign ID>",
		"<proposal ID 3>": "<Space Name>/campaign/<Campaign ID>",
	}
}
```

{% hint style="warning" %}
If you delete a `proposalID-campaignInfo` pair, users won’t see the OAT information on the page of your proposal even if the proposal has ended or the OATs have already been distributed.
{% endhint %}

### 4. Confirm and save space settings

Click **Add** and scroll up to the top of the page to click **Save** to persist the updated settings.

That's it, your users will be able to see the Galxe plugin on the proposal's page!

{% hint style="info" %}
You can edit the configuration of your plugin in order to add new proposals to the list. Simply go to settings and click the Galxe plugin to edit the JSON with details. Don't forget to save your settings!
{% endhint %}
