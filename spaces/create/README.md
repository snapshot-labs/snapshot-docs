---
description: To create a space in Snapshot follow these steps.
---

# Create a space

{% hint style="info" %}
If you already have a space without ENS domain (legacy), you need to [Migrate your space to ENS](https://docs.snapshot.page/spaces/migrate).
{% endhint %}

### 1. Set or get an ENS domain for your space

Tap the plus (+) button in the left sidebar to start creating your space.

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 12.30.46.png>)

If you already own an ENS domain, make sure you are connected to [snapshot.org](https://snapshot.org/#/setup) with the Ethereum address that is set as controller of your ENS name. Your ENS name will appear and you will be started by tapping on it.\
\
If you need to register an ENS domain, enter a name that suit the needs of your DAO in the `register a new domain` field and tap register, you can then follow [before-creating-your-space.md](before-creating-your-space.md "mention") and come back here for step 2 once registered.\
\


### 2. Set space controller (ENS text-record)

By default the address of the currently logged account is pre-filled, you can customize it by tapping on the switcher then entering the wallet address that you would like to set as the space controller and click "Set controller". &#x20;

{% hint style="info" %}
You will need to sign a transaction on the Ethereum Mainnet to set the ENS text-record.&#x20;
{% endhint %}

![Set the ENS text-record to determine the space controller](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 12.31.58.png>)

### 3. Create your profile

To complete your profile, you can upload an avatar/logo, enter a name for your DAO (mandatory), a description, select a category and some other details. These settings can be changed later in your space settings.

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 12.53.39.png>)

### **4. Set your very first strategy**

At this stage, you have to choose one the three following ways to implement the strategy that will define how the voting power of your voters is fetched.

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 12.33.32.png>)

### Let's see those three options in detail&#x20;

#### Token weighted voting

Votes are weighted by a token. The token can be an ERC-20, ERC-721 or ERC-1155 token standard

1. Select your token network
2. Select your token standard
3. Enter your token contract address

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 12.37.27.png>)

#### One person, one vote

This option can be used in two different ways:

* Whitelist voting let you specify a list of addresses that will be able to vote
* Ticket voting will let any wallet vote (mostly for testing purpose)

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 13.24.40.png>)

#### Custom setup

If you feel ready to deep dive in the custom setup here are a few hints that you may find useful:\
\
\- You can select up to 8 strategies, voting power is cumulative.\
\- Network can be selected independently for each strategy to achieve multi-chain.\
\- You can set a different symbol for each strategy, it will be displayed on the details of a vote.\
\
At the time of writing this article Snapshot count around 350 strategies and this number keep increasing. [Learn more about the strategies. ](../../strategies/what-is-a-strategy.md)

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 13.25.04 (1).png>)

## Moderation

**Admins** will be able to edit the space settings and moderate proposals.&#x20;

**Authors** will be able to create proposals without being constrained by filters. Make sure that members specified in authors field are allowed to submit a proposal.

{% hint style="info" %}
You must add one address per line.
{% endhint %}

![](<../../.gitbook/assets/Capture d’écran 2022-08-12 à 13.53.21.png>)

## Your space is live !

![](<../../.gitbook/assets/Capture d’écran 2022-08-12 à 13.53.39.png>)

### What can I do now**?**

{% content-ref url="../add-custom-domain.md" %}
[add-custom-domain.md](../add-custom-domain.md)
{% endcontent-ref %}

{% content-ref url="../add-skin.md" %}
[add-skin.md](../add-skin.md)
{% endcontent-ref %}
