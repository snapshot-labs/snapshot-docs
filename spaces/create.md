---
description: To create a space in Snapshot follow these steps.
---

# Create a space

{% hint style="info" %}
If you already have a space without ENS domain (legacy), you need to [Migrate your space to ENS](https://docs.snapshot.page/spaces/migrate).
{% endhint %}

### 1. Get an ENS domain for your space

If you haven't already, follow this guide - [https://docs.snapshot.org/spaces/before-creating-your-space](https://docs.snapshot.org/spaces/before-creating-your-space) to get your ENS domain.

Now that you have a ENS address go ahead and setup your space on [snapshot.org](https://snapshot.org/#/setup)

![Click the plus button in the sidebar and then click you ENS address you just setup](<../.gitbook/assets/image (1) (1).png>)

### 2. Set ENS text-record

![Set the ENS text-record to determine the space controller](<../.gitbook/assets/image (7).png>)

Enter the wallet address that you would like to set as the space controller and click "Set controller".&#x20;

{% hint style="info" %}
You will need to sign a transaction on the Ethereum Mainnet to set the ENS text-record.
{% endhint %}

### 3. Create space

![](<../.gitbook/assets/image (6).png>)

To create your space you will need to enter a name, symbol and selected a network. These settings can be changed in your space settings.

### **4. Customize your space settings**

If you have trouble finding the settings page you can manually navigate to it with the following URL:&#x20;

`https://snapshot.org/#/`**`<ENS DOMAIN>`**`/settings`

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

#### Filters

* **Proposal threshold** is the minimum number of tokens required to create a proposal.
* **Proposal validation** is a custom function to validate if someone can post a proposal or not. You can use the basic validation by default which takes your voting power with space strategies and checks if you pass a defined threshold.

![](<../.gitbook/assets/Capture d’écran 2022-02-22 à 12.33.34.png>)

**Allow only authors to submit a proposal,** authors will be able to create proposals without being constrained by filters. You must add one address per line. Makes sure that only members specified in authors field are allowed to submit a proposal.&#x20;

![Add authors' addresses](<../.gitbook/assets/Capture d’écran 2022-02-22 à 12.26.04.png>)

####

#### Plugins

Plugins give extra features for your space. More information here:

{% content-ref url="../plugins/" %}
[plugins](../plugins/)
{% endcontent-ref %}

### 5. Save your settings

Click "**Save**" then confirm the action in your wallet.

You are all set! You can go on `https://snapshot.org/#/<ENS_DOMAIN>` to see your space.

### What you can do now**?**

{% content-ref url="add-skin.md" %}
[add-skin.md](add-skin.md)
{% endcontent-ref %}

{% content-ref url="add-custom-domain.md" %}
[add-custom-domain.md](add-custom-domain.md)
{% endcontent-ref %}
