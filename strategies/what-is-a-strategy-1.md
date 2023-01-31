# Validation strategies

## What is a validation strategy?

A voting validation is a JavaScript function that returns a boolean (`true` or `false`) for the connected account. Voting validations are being used on Snapshot to decide if an **account can vote** or **create a proposal** in a specific space**.** Each space can use one voting validation for all of its proposals at a time. While voting strategies calculate the Voting Power mainly on the basis of the monetary assets, the validation strategy can serve as a protection against **Sybil attacks**. It can take into consideration how many POAPs an account owns or track the account activity to assess if the account is a bot or a **real human**.

The **default** validation is checking if the address has **any voting power.** If the voting power is higher than `0` the connected account is validated. A validation strategy can send a call to a node or subgraph.

## How to use validation strategies:

Validation strategies can be used for two purposes:

* proposal validation - determine if the account can create a new proposal,
* voting validation - determine if the account can take part in the voting process.

If you want to allow addresses with any voting power to create a proposal or vote you can use the default voting validation.

![](<../.gitbook/assets/image (1) (1) (2).png>)

## Validation strategy example - Gitcoin Passport

Validation strategy built together with **Gitcoin Passport.** You can select individual or multiple stamps that matter for your space. You can also decide if they need to meet all of these criteria or only one. The more criteria you select, the more sybil resistant your space is.



![](<../.gitbook/assets/image (17).png>)



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

The possibilities are endless! You can build a custom validation strategy for your space. Please have a look at [create-1-1.md](../guides/create-1-1.md "mention")for more details.

## Find more voting validations here: <a href="#find-more-strategies-here" id="find-more-strategies-here"></a>

{% embed url="https://github.com/snapshot-labs/snapshot-strategies/tree/master/src/validations" %}
