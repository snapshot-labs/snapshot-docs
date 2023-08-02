# Validation strategies

{% hint style="info" %}
Due to many spam attacks on Snapshot all Spaces are now required to use **Proposal validation**.\
\
Learn how to set it up on this page or read [**our article**](https://snapshot.mirror.xyz/-uSylOUP82hGAyWUlVn4lCg9ESzKX9QCvsUgvv-ng84)**.**\
\
If you see this error it means your space doesn't have any Proposal validation:

\
<img src="../../.gitbook/assets/image (5) (3).png" alt="" data-size="original">
{% endhint %}

{% hint style="info" %}
Spaces using only a [ticket strategy](https://snapshot.org/#/strategy/ticket) are required to set a Voting validation to secure their spaces and ensure a fair voting process preventing spam.\
\
Learn here how to set it up: [#voting-validation-in-space-settings](validation-strategies.md#voting-validation-in-space-settings "mention")\
\
If you see this error it means your space has to set up the Validation:\
![](<../../.gitbook/assets/image (7).png>)
{% endhint %}

## What is a validation strategy?

A voting validation is a JavaScript function that returns a boolean (`true` or `false`) for the connected account. Voting validations are being used on Snapshot to decide if an **account can vote** or **create a proposal** in a specific space**.** Each space can use one voting validation for all of its proposals at a time. While voting strategies calculate the Voting power mainly on the basis of the monetary assets, the validation strategy can serve as a protection against **Sybil attacks**. It can take into consideration how many POAPs an account owns or track the account activity to assess if the account is a bot or a **real human**.

The **default** validation is checking if the address has **any voting power.** If the voting power is higher than `0` the connected account is validated. A validation strategy can send a call to a node or subgraph.

When setting the Validation strategy up it’s important to keep in mind that it is **meant to make it difficult for users outside of your community to post scam proposals or post spam votes.**

Therefore for Proposal validation make sure to use a **high threshold**, for example $100 worth of your organization’s token. A good idea would be to check the holdings of previous proposal creators, both legitimate and scammers, to assess a reasonable value.

## How to use validation strategies:

Validation strategies can be used for two purposes:

* proposal validation - determine if the account can create a new proposal,
* voting validation - determine if the account can take part in the voting process.

#### Proposal validation in Space settings

Head to **Proposals** tab in the sidebar to update the configuration:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-01 at 12.44.17.png" alt=""><figcaption></figcaption></figure>

#### Voting validation in Space settings

Head to **Voting** tab in the sidebar to update the configuration:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-01 at 12.44.57.png" alt=""><figcaption></figcaption></figure>

If you want to allow addresses with any voting power to vote you can use the default voting validation.

<figure><img src="../../.gitbook/assets/image (1) (1) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If you are using only a [ticket](https://snapshot.org/#/strategy/ticket) Voting strategy for your space you are required to use a [Gitcoin Passport Validation](validation-strategies.md#validation-strategy-example-gitcoin-passport) for Voting to protect your space from spam votes.
{% endhint %}

## Authors only mode

If you wish to limit proposal creators to Admins, Moderators and Authors only, you can do so by enabling the **Authors only** setting in the **Proposal** tab in the space settings. Make sure to give the Author role to the users you trust!

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-01 at 12.22.46.png" alt=""><figcaption></figcaption></figure>

## Validation strategy example - Basic

The Basic validation strategy allows you to use existing Voting strategies configured for your space or define a custom setup to determine if a user is eligible to create a proposal or cast a vote.&#x20;

In order to use existing setup of Voting strategies you can simply chose **Basic Validation** and define a required threshold as on the screenshot below. `100` corresponds to user's Voting power calculated on the basis of the Voting strategies.

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-01 at 12.16.21.png" alt=""><figcaption><p>Use current setup and define a strong threshold to avoid spam in your space.</p></figcaption></figure>

If you wish to use a different configuration, toggle the **Use custom strategies** button and define the strategies for your use case:

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-01 at 12.18.16.png" alt=""><figcaption><p>Use a custom setup using various Voting strategies to calculate if a user is eligible to create a proposal or vote.</p></figcaption></figure>

## Validation strategy example - Gitcoin Passport

Validation strategy built together with **Gitcoin Passport.** You can select individual or multiple stamps that matter for your space. You can also decide if they need to meet all of these criteria or only one. The more criteria you select, the more sybil resistant your space is.



<figure><img src="../../.gitbook/assets/image (17) (2) (1).png" alt=""><figcaption></figcaption></figure>



#### Implementation

Have a look at the example of the Gitcoin Passport validation strategy.

{% embed url="https://github.com/snapshot-labs/snapshot-strategies/blob/master/src/validations/passport-gated/index.ts" %}

```javascript
import snapshot from '@snapshot-labs/snapshot.js';
import Validation from '../validation';
import {
  getPassport,
  getVerifiedStamps,
  hasValidIssuanceAndExpiration
} from '../passport-weighted/helper';

export default class extends Validation {
  public id = 'passport-gated';
  public github = 'snapshot-labs';
  public version = '0.1.0';

  async validate(): Promise<boolean> {
    const requiredStamps = this.params.stamps;
    const passport: any = await getPassport(this.author);
    if (!passport) return false;
    if (!passport.stamps?.length || !requiredStamps?.length) return false;

    const verifiedStamps: any[] = await getVerifiedStamps(
      passport,
      this.author,
      requiredStamps.map((stamp) => ({
        id: stamp
      }))
    );
    if (!verifiedStamps.length) return false;

    const provider = snapshot.utils.getProvider(this.network);
    const proposalTs = (await provider.getBlock(this.snapshot)).timestamp;

    const operator = this.params.operator;

    // check issuance and expiration
    const validStamps = verifiedStamps
      .filter((stamp) =>
        hasValidIssuanceAndExpiration(stamp.credential, proposalTs)
      )
      .map((stamp) => stamp.provider);

    if (operator === 'AND') {
      return requiredStamps.every((stamp) => validStamps.includes(stamp));
    } else if (operator === 'OR') {
      return requiredStamps.some((stamp) => validStamps.includes(stamp));
    } else {
      return false;
    }
  }
}
```

Voting validation can be specified in your space settings at `https://snapshot.page/#/<SPACE ADDRESS>/settings`.&#x20;

## Create a custom validation&#x20;

The possibilities are endless! You can build a custom validation strategy for your space. Please have a look at [validation-strategy.md](../../developer-guides/create-a-strategy/validation-strategy.md "mention")for more details.

## Find more voting validations here: <a href="#find-more-strategies-here" id="find-more-strategies-here"></a>

{% embed url="https://github.com/snapshot-labs/snapshot-strategies/tree/master/src/validations" %}
