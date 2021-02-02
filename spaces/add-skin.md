---
description: Skins are optional.
---

# Add a skin

To create your own skin you need to do a pull request on this repository:

{% embed url="https://github.com/snapshot-labs/snapshot-spaces" %}

#### Follow the Snapshot skins directory tree

```bash
└── skins
    └── my-space.scss
```

### Add your skin

To add your skin you will need to create a "my-space.scss" file in the "skins" directory.

```css
.my-space {
  --primary-color: #384aff;
  --bg-color: white;
  --text-color: #586069;
  --link-color: #111111;
  --heading-color: #111111;
  --border-color: #d1d5da;
  --header-bg: white;
  --block-bg: transparent;
}
```

{% hint style="danger" %}
Change the file name **my-space.scss** and css selector **.my-space** with your space name.
{% endhint %}

Select then your skin in the Skin field in your space settings.

![Snapshot skin selector.](../.gitbook/assets/capture-de-cran-2020-12-30-a-09.33.58.png)

{% hint style="info" %}
After committing your PR, you will have to wait for the merge and the deployment of your PR to be able to select your skin available. This process can take a few hours.
{% endhint %}

