---
description: Follow this guide if you have a space on Snapshot without an ENS name.
---

# Migrate your space to ENS

If you already have a space on Snapshot which does not have an ENS name, you need to migrate your space to ENS by following the steps below:

## 1. Create a space with ENS

To migrate your space you will need first to create a new space with an ENS domain.&#x20;

{% content-ref url="create/" %}
[create](create/)
{% endcontent-ref %}

## 2. Map your old space alias to the ENS

### 2a. Fork the snapshot-spaces repository

Fork the below repository to make changes needed to mirate your space.

{% embed url="https://github.com/snapshot-labs/snapshot-spaces" %}

### 2b. Link your old space alias to ENS

Open the [aliases.json file](https://github.com/snapshot-labs/snapshot-spaces/blob/master/spaces/aliases.json) and add the alias of the space you wish to migrate together with the newly ENS domain name of the newly created space as in the example below:

```javascript
"my-space": "my-space.eth"
```

### 2c. Create a Pull Request

Create a Pull Request on the original [snapshot-spaces](https://github.com/snapshot-labs/snapshot-spaces/) repository with the above changes.

It can take the team around **72 hours** to merge your Pull Request, so please be patient :pray:

Once the PR is merged you will have to wait for the release of a new version on [https://snapshot.org](https://snapshot.org). It can take up to a **couple of days**. Once the new version is released you can move on to the next step.

## 3. Migrate proposals, votes and URLs

Now the Snapshot team has to migrate your old space to the new one.

Contact our support on [Help Center](https://help.snapshot.org/en/) to start the migration.

You have now successfully migrated your space to ENS! :tada:
