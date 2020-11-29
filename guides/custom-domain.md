---
description: Please ask the team for validating a custom domain
---

# Custom domain

## **1: Add the domain here**

[https://github.com/bonustrack/snapshot-spaces/blob/master/spaces/domains.json](https://github.com/bonustrack/snapshot-spaces/blob/master/spaces/domains.json)

`domains.json`

```javascript
{
  "my.custom.url": "my-space-key"
}
```

{% hint style="info" %}
Check that you have the `domain` field in the `index.json` file of your space following the documentation to create a space in the paragraph[ **Space metadata**](../archived/create-a-space-github.md#3-space-metadata).
{% endhint %}

## **2: Configure the DNS**

You will need to add this as CNAME in your domain DNS `snapshotpage.b-cdn.net`

