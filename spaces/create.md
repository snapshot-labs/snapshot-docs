---
description: To create a space in Snapshot follow these steps.
---

# Create a space

{% hint style="info" %}
If you already have a space without ENS domain (legacy), you need to [Migrate your space to ENS](https://docs.snapshot.page/spaces/migrate).
{% endhint %}

{% embed url="https://www.youtube.com/watch?v=oa6WCvnWLBc" %}

### 1. Get an ENS domain for your space

If you haven't already, follow this guide - [https://docs.snapshot.org/spaces/before-creating-your-space](https://docs.snapshot.org/spaces/before-creating-your-space) to get your ENS domain.&#x20;

### 2. Link your ENS domain to Snapshot

Once you have created your ENS domain, Go to this url and modify the tag with your ENS domain. `https://snapshot.org/#/`**`<ENS DOMAIN>`**`/settings` and login with the wallet that owns the ENS domain.

![Access your space settings](../.gitbook/assets/access-to-your-space-settings.png)

Once connected, the **\<your-address>** tag will be replaced with your wallet address.

{% hint style="info" %}
You will need a wallet that can sign message like MetaMask, Fortmatic, Portis, Argent. Don't use a Gnosis Safe has they are currently not supported.
{% endhint %}

![Set your Snapshot IPNS link](../.gitbook/assets/set-your-ipns-link.png)

If you are on your domain space and connected with your wallet you will see the correct **IPNS link** in the **ENS field**. Click on the button **Set record on ENS**, and you will get redirected to ENS page.

* On the ENS page, click on **ADD/EDIT RECORD**.
* Select **TEXT** and type the key **"snapshot"** in lowercase.
* Paste the **IPNS link** in the field.
* Click **Save**.
* Scroll down and click **Confirm**.
* Sign the transaction with your wallet.

![](<../.gitbook/assets/snapshot (2).gif>)

### **3. Setup your space settings**

Refresh the Snapshot settings page `https://snapshot.org/#/`**`<ENS DOMAIN>`**`/settings` to see the space setting.

#### Profile

![](../.gitbook/assets/profile-settings.png)

* **Name** is the name that will be displayed in your space.
* **About** is the description of your governance purposes.
* **Avatar** is your project logo.
* **Network** must be the network relative to your token.

![Select a network](../.gitbook/assets/select-a-network.png)

* **Symbol** is the main token symbol that will be displayed in your space.
* **Skin** can be left as a default, used as an existing one or you can [create your own skin](add-skin.md).

![Select a skin](../.gitbook/assets/select-a-skin.png)

* **Twitter** and **Github** just add a username to link to your different accounts.
* **Domain name** is optional but you can [add a custom domain](add-custom-domain.md).
* **Terms** links to your website's terms and conditions.
* **Hide space from homepage** if you want to keep your space "private".

#### **Strategies**

A strategy is a JavaScript function that defines how the voting power is calculated. You need to add a voting strategy for your proposals. erc20-balance-of is the most used strategy.  You can have multiple strategies and can have your custom strategies as well.&#x20;

You need to add a voting strategy for your proposals. `erc20-balance-of` is the most common strategy.

![Add a strategy](../.gitbook/assets/add-a-strategy.png)

{% hint style="info" %}
You can add up to 5 strategies in your space.
{% endhint %}

Once selected, you can edit the strategy by clicking on it if you want to add your own token.

![](../.gitbook/assets/edit-a-strategy.png)

More information here:

{% content-ref url="../strategies/" %}
[strategies](../strategies/)
{% endcontent-ref %}

#### Admins

The admins will be able to edit the space settings and moderate proposals. You must add one address per line.

![Add admins' addresses](../.gitbook/assets/add-admins-addresses.png)

#### Members

Members will be able to create proposals without being constrained by filters. You must add one address per line.

![Add members' addresses](../.gitbook/assets/add-members-addresses.png)

#### Filters

* **Proposal threshold** is the minimum number of tokens required to create a proposal.
* **Proposal validation** is a custom function to validate if someone can post a proposal or not. You can use the basic validation by default which takes your voting power with space strategies and checks if you pass a defined threshold.
* **Allow only members to submit a proposal** makes sure that only members specified in members field are allowed to submit a proposal.&#x20;

![](../.gitbook/assets/screenshot-179-.png)

#### Plugins

Plugins give extra features for your space. More information here:

{% content-ref url="../plugins/" %}
[plugins](../plugins/)
{% endcontent-ref %}

### 4. Save your settings

Click "**Save**" then confirm the action in your wallet.

You are all set! You can go on `https://snapshot.org/#/<ENS_DOMAIN>` to see your space.

### What you can do now**?**

{% content-ref url="add-skin.md" %}
[add-skin.md](add-skin.md)
{% endcontent-ref %}

{% content-ref url="add-custom-domain.md" %}
[add-custom-domain.md](add-custom-domain.md)
{% endcontent-ref %}
