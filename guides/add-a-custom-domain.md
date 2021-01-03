---
description: Custom domain is optional.
---

# Add a custom domain

To add a custom domain you need to do a pull request on this repository:

{% embed url="https://github.com/snapshot-labs/snapshot-spaces" %}

#### Follow the Snapshot spaces directory tree

```bash
└── spaces
    └── domains.json
```

### Add a custom domain

#### Set it in the Domain name field

To add a custom domain, fill in the Domain name field in your settings.

![Domain name field in Snapshot settings.](../.gitbook/assets/capture-de-cran-2020-12-30-a-09.34.49.png)

#### Insert it in the domains list

You must then add your domain in the [domains.json file](https://github.com/snapshot-labs/snapshot-spaces/blob/master/spaces/domains.json) by following this example.

```javascript
{
  "my.custom.url": "my-space.eth"
}
```

#### Configure your DNS 

You will need to add this as CNAME in your domain DNS `snapshotpage.b-cdn.net`

{% hint style="info" %}
After committing your PR, you will have to wait for the merge and the deployment of your PR to be able to get your domain live. This process can take a few hours.
{% endhint %}

