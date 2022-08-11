# Settings

## Access your settings

Tap on the Settings menu on your space

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.07.53.png>)

{% hint style="info" %}
If you have trouble finding the settings page you can manually navigate to it with the following URL: https://snapshot.org/#/\<YOUR-ENS-NAME>/settings
{% endhint %}

## Edit the controller of your space

To replace the current space controller by a new controller tap on Edit controller

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.14.17.png>)

{% hint style="info" %}
You will need to sign a transaction on the Ethereum Mainnet to edit the ENS text-record.&#x20;
{% endhint %}

## Edit your profile

To complete your profile, you can upload an avatar/logo, enter a name for your DAO, a description, select a category and some other details. Settings can be changed at any time.

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.20.57.png>)

## Social accounts

Just add a username to link to your different accounts

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.30.17.png>)

## Sub-spaces

If you are editing the settings of your main space, add your sub-spaces. If you are editing the settings of your sub-space, add your main space.&#x20;

[Find out more about sub-spaces](sub-spaces.md)

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.30.37.png>)

## Voting strategies

A strategy is a JavaScript function that defines how the voting power is calculated. ERC20-balance-of is the most used strategy. You can use multiple strategies and can write your custom strategies as well.

\- You can select up to 8 strategies, voting power is cumulative.\
\- Network can be selected independently for each strategy to achieve multi-chain.\
\- You can set a different symbol for each strategy, it will be displayed on the details of a vote.

{% hint style="info" %}
At the time of writing this article Snapshot count around 350 strategies and this number keep increasing. [Learn more about the strategies. ](../strategies/what-is-a-strategy.md)
{% endhint %}

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.31.08.png>)

## Admins and authors

**Admins** will be able to edit the space settings and moderate proposals.&#x20;

**Authors** will be able to create proposals without being constrained by filters. Make sure that members specified in authors field are allowed to submit a proposal.

You must add one address per line.

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.31.29.png>)

## Proposal validation

To validate if someone can post a proposal or not you can use the basic validation by default which takes your voting power with space strategies and checks if you pass a defined threshold.

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.31.47.png>)

## Voting

The voting delay is a value in time for which the proposal is in pending state, before the active state of the proposal when voters are able to cast a vote. The voting period is the duration of the active state before the proposal get closed.

Quorum is the amount of voting power collectively achieved by voters for a proposal to pass, if the quorum is not met, proposal is invalid.

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.32.03.png>)

## Custom domain

You can add a custom domain by following this [guide](add-custom-domain.md).

Skin require a custom domain and will not effect the UI on snapshot.org

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.32.30.png>)

## Treasuries

Choose a network, enter an Ethereum address and name that treasury. You can add multiple treasuries. &#x20;

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.32.50.png>)

## Plugins

Plugins give extra features for your space. More information here:​ [Plugins](../plugins/)

![](<../.gitbook/assets/Capture d’écran 2022-08-11 à 14.33.20.png>)

## Save your settings

Click "Save" then confirm the action in your wallet.You are all set!
