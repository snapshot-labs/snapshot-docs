---
description: >-
  Customize your space settings, sub-spaces, manage access, voting strategies
  and validation and more!
---

# Settings

## Access your settings

Navigate to your space settings from the space menu by clicking on `Settings`.

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.07.53.png>)

{% hint style="info" %}
If you have trouble finding the settings page you can manually navigate to it with the following URL: https://snapshot.org/#/\<YOUR-ENS-NAME>/settings
{% endhint %}

## Edit the controller of your space

Space controller is the main account that is able to manage the space settings and assign other addresses as admins of the space. By default it's set as the ENS Controller address however you can change it to another address.&#x20;

To replace the current space controller by a new controller click the `Edit controller` button.

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.14.17.png>)

{% hint style="info" %}
You will need to **sign a transaction** on the Ethereum Mainnet to set the ENS text-record.&#x20;
{% endhint %}

## Edit your profile information

To complete your profile, you can upload an avatar/logo, enter a name for your DAO, a description, select up to 2 categories and other details. These settings can be changed at any time.

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.20.57.png>)

## Social accounts

You can link your social media accounts to the space on Snapshot by typing in your account handle, i.e. [@SnapshotLabs ](https://twitter.com/SnapshotLabs)

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.30.17.png>)

## Sub-spaces

{% hint style="info" %}
If you don't know what a sub-space is head to [sub-spaces.md](sub-spaces.md "mention") to learn more about them!
{% endhint %}

In order to connect the space with sub-spaces you need to set them up for both main- and the sub-space.

1. First **create the sub-space** as you would create a normal space. Once the sub-space is set up, type it's linked ENS domain name in the Sub-spaces input field. If everything went well, you will be able to click the **`+`** on the right.
2. Head to the sub-space settings and type in the linked ENS domain name of the **voting** in the correct input field.

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.30.37.png>)

{% hint style="warning" %}
If you see a  ❌  after typing the sub-space name it means that it cannot be found. Make sure that you have created the sub-space before adding it.
{% endhint %}

## Voting strategies

Specify how the voting power should be calculated by adding one or up to 8 strategies.

To learn more about what they are and how they work head to [voting-strategies.md](../strategies/voting-strategies.md "mention").

{% hint style="danger" %}
If you are using a [ticket](https://snapshot.org/#/strategy/ticket) strategy which gives everyone 1 vote regardless of their holdings, you are required to set up a Voting Validation. \
\
Head here to learn how to do it: [#validation-strategy-example-gitcoin-passport](../strategies/validation-strategies.md#validation-strategy-example-gitcoin-passport "mention")
{% endhint %}

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.31.08.png>)

## Admins and authors

In order to specify who can manage the space or create proposals, fill in the apropriate field with addresses for:

* **Admins** - able to edit the space settings and moderate proposals.&#x20;
* **Authors** - able to create proposals without any constraints Make sure that members specified in authors field are allowed to submit a proposal.

{% hint style="info" %}
Each line should be populated with one address only. Do not add multiple addreses in one line and do not use separators like commas, dots or semicolons.\
\
You can add up to 100 addresses in each field.
{% endhint %}

Head to [space-roles.md](space-roles.md "mention") to learn more about each role.

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.31.29.png>)

##

## Proposals

You can provide guidelines and a template which will be displayed during the proposal creation:

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Proposal validation

{% hint style="danger" %}
Due to multiple spam attacks on Snapshot each space is now required to set up a **Proposal Validation**.\
\
Learn how to do it in [#how-to-use-validation-strategies](../strategies/validation-strategies.md#how-to-use-validation-strategies "mention")
{% endhint %}

To validate if someone can post a proposal or not you can use the basic validation by default which takes your voting power with space strategies and checks if you pass a defined threshold.

To learn what a validation is head to [validation-strategies.md](../strategies/validation-strategies.md "mention").

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.31.47.png>)

## Voting

The **voting delay** is a value in time between the time of proposal creation and the moment when users are allowed to vote. \
The **voting period** is the duration that the proposal is active and votes can be cast. It is counted from the moment&#x20;

**Quorum** is the amount of voting power collectively achieved by voters which is required for a proposal to pass.

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.32.03.png>)

### Shielded Voting

You can enable Shielded Voting within your space if you want to enable partial privacy and reduce voter apathy. Shielded Voting designed by Shutter is enabling that by using threshold encryption. You can learn more about it in the [technical overview.](https://blog.shutter.network/shutter-brings-shielded-voting-to-snapshot/)

In short, Shielded Voting is a voting setting in which the voters choices are private during the voting period and get revealed when the proposal closes.

To enable it head to **Voting** tab and select Shutter within the **Privacy** setting.&#x20;

<figure><img src="../../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>

## Delegation

In the **Delegation** tab you can set a custom delegation contract to enable delegate discovery for your space:

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-30 at 13.17.08.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Once set, the delegates registry will be visible in the **Delegates** tab in the Space page.
{% endhint %}

## Custom domain and skin

You can add a custom domain to your space by following the [add-custom-domain.md](add-custom-domain.md "mention") guide.

If you want to apply a different design (skin) to your space, you have to set a custom domain first. Head to [add-skin.md](add-skin.md "mention") to learn how to add a custom skin for your custom domain.

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.32.30.png>)

## Treasuries

In order to link your organization's treasury to Snapshot you have to:

1. Choose the treasury network
2. Enter its Ethereum address
3. Fill in the name of that treasury.&#x20;

It is possible to add multiple treasuries to one space. &#x20;

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.32.50.png>)

## Plugins

You can customize your space even further with various plugins which provide extra features. To learn more about the plugins head to [plugins](../plugins/ "mention") section.&#x20;

![](<../../.gitbook/assets/Capture d’écran 2022-08-11 à 14.33.20.png>)

## Save your settings

Make sure to click the `Save` button on top of the settings page to apply the changes to your space. Once you **sign a message** (gasless) in your wallet, changes will be applied!
