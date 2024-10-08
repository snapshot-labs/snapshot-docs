---
description: >-
  This page guides you step by step through the process of creating a space for
  your organization.
---

# Create a space

{% hint style="danger" %}
If you already have a space without ENS domain (legacy), you need to [Migrate your space to ENS](https://docs.snapshot.page/spaces/migrate).
{% endhint %}

{% hint style="info" %}
If you want to use Snapshot in a demo mode to experiment with the platform head to [https://testnet.snapshot.org](https://testnet.snapshot.org) - our playground connected to the Goerli Testnet. Make sure to provide an ENS name registered on Goerli Testnet in the first step below.
{% endhint %}

### 1. Set or get an ENS domain for your space

Tap the plus **`+`** button in the left sidebar to create a new space.

![](<../../../.gitbook/assets/Capture d’écran 2022-08-11 à 12.30.46.png>)

If you already own an ENS domain, make sure you are connected to [snapshot.org](https://snapshot.org/#/setup) with the **Ethereum address** that is set as **controller of your ENS name** (if you are confused about the difference between ENS Registrant and Controller, have a read [here](https://docs.ens.domains/permanent-registrar-faq#what-is-the-registrant-and-controller-of-a-name)).&#x20;

If the above condition is met, your ENS name will appear. To confirm it's correct, click on it.\
\


{% hint style="info" %}
If you **don't own an ENS domain** you will have to register one. \
\
Enter a name that suits the needs of your DAO in the `register a new domain` field and click `Register.` You can then follow [ens-domain.md](ens-domain.md "mention") and come back here for step 2 once domain has been registered.
{% endhint %}

### 3. Create your profile

To complete the profile of your space you have to enter a name for your DAO (mandatory) and can add further optional information like a description, avatar, categories describing the field that your DAO is operating in and more.&#x20;

You can add or update this information after you have finished creating the space.

![](<../../../.gitbook/assets/Capture d’écran 2022-08-11 à 12.53.39.png>)

### **4. Set your very first strategy**

Your space can combine up to 8 voting strategies which will be responsible for calculating the users' voting power. The setting affects all proposals that will be created for that space.&#x20;

{% hint style="info" %}
If you would like to differentiate the calculation of users' voting power between proposals you will have to create a sub-space. Head to [sub-spaces.md](../sub-spaces.md "mention") to learn more.
{% endhint %}

For the initial setup you have to choose one of the three following strategy types to then specify the strategy details:

![](<../../../.gitbook/assets/Capture d’écran 2022-08-11 à 12.33.32.png>)

### Voting strategies types&#x20;

Let's have a look at each of the possible options and see how you can specify the strategy details.

{% hint style="info" %}
Each strategy is taking into account the assets that belong to the voting address **at the time of proposal creation**, not at the time of voting.
{% endhint %}

#### Token weighted voting

Voting power is weighted by the amount of the token held by the user. The token can be an ERC-20, ERC-721 or ERC-1155 token standard.

1. Select your token network
2. Select your token standard
3. Enter your token contract address

<div align="center">

<img src="../../../.gitbook/assets/Capture d’écran 2022-08-11 à 12.37.27.png" alt="">

</div>

#### One person, one vote

This option can be used in two different ways:

* **Whitelist voting** lets you specify a list of addresses that will be able to vote
* **Ticket voting** will let any wallet vote (option used mostly for testing purposes)

![](<../../../.gitbook/assets/Capture d’écran 2022-08-11 à 13.24.40.png>)

#### Custom setup

If you feel ready to dive deeper into the custom setup here are a few hints that you may find useful:

* You can select up to 8 different strategies. Voting power is cumulative.
* Network can be selected individually for each strategy. This way you can leverage multi-chain voting power calculation.
* It is possible to set a different symbol for each strategy. They will be displayed on the proposal page.
* You can write a custom voting strategy if the existing ones are the sufficient for your needs. Have a look at [voting-strategy.md](../../../developer-guides/create-a-strategy/voting-strategy.md "mention") to learn more.

\
At the time of writing this article there are around 415 Snapshot voting strategies and this number keeps growing. [Learn more about the strategies. ](../../strategies/voting-strategies.md)

![](<../../../.gitbook/assets/Capture d’écran 2022-08-11 à 13.25.04.png>)

## Moderation

**Admins** will be able to edit the space settings and moderate proposals.&#x20;

**Authors** will be able to create proposals without any constraints like proposal validation. Make sure that members specified in authors field are allowed to submit a proposal.

{% hint style="info" %}
You can add between 1 and 100 addresses. Each line should be an individual address - do not list multiple addresses in on line with any characters like commas, dots or semicolons.
{% endhint %}

![](<../../../.gitbook/assets/Capture d’écran 2022-08-12 à 13.53.21.png>)

## Your space is live !

![](<../../../.gitbook/assets/Capture d’écran 2022-08-12 à 13.53.39.png>)

### What else can I customize?

{% content-ref url="../add-custom-domain.md" %}
[add-custom-domain.md](../add-custom-domain.md)
{% endcontent-ref %}

{% content-ref url="../add-skin.md" %}
[add-skin.md](../add-skin.md)
{% endcontent-ref %}
