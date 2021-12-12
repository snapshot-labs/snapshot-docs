---
description: Custom domain is optional.
---

# Add a custom domain

As you already have a domain with ENS, adding a custom domain is optional. Custom domain allows you to display your space (and only your space) on a custom domain. E.g., **** [https://vote.balancer.fi/#/](https://vote.balancer.fi/#/)

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

#### Insert it in the domains**.json file** list

To add your subdomain to Snapshot, you need to **edit the** **domains.json** file below.

{% embed url="https://github.com/snapshot-labs/snapshot-spaces/blob/master/spaces/domains.json" %}
Add you custom domain in the domains.json file
{% endembed %}

{% hint style="warning" %}
To prevent conflicts, it is recommended to add your subdomain between two existing domains rather than at the end or beginning of the list, as in the example below.
{% endhint %}

```javascript
{
  ...
  "other.domain.com": "ens.eth",
  "my.custom.url": "my-space.eth",
  "other.domain.com": "ens.eth",
  ...
}
```

#### Configure your DNS&#x20;

You will need to add this as CNAME in your domain DNS `snapshotpage.b-cdn.net`

After committing your PR, you will have to wait for the merge and the deployment of your PR to be able to get your domain live. This process can take a few hours.

Once the PR is merged you can go here to activate the domain:\
[https://ina9pk8175.execute-api.us-west-2.amazonaws.com/dev?domain=example.com](https://ina9pk8175.execute-api.us-west-2.amazonaws.com/dev?domain=example.com)\
(Replace "example.com" with your custom domain).
