---
description: Create your own space on Snapshot!
---

# Create a space

## **1: Fork Snapshot spaces repository here**

{% embed url="https://github.com/bonustrack/snapshot-spaces" caption="" %}

## **2: Copy the space example folder**

{% embed url="https://github.com/bonustrack/snapshot-spaces/tree/master/spaces/example" caption="" %}

```text
|-- spaces
    |-- example
        |-- index.json
        |-- logo.png
        |-- skin.scss
        |-- space.png
```

## **3: Change your space metadata**

* The name of the folder must be the key of your space.
* This key also corresponds to the slug url and must not be composed with uppercase characters. `"key": "example"` to `"key": "my-space"`

`index.json`

```javascript
{
  "key": "example", // This will be the url of your space
  "name": "Example", // Name of the space (max 12 chars)
  "chainId": 1, // ID of the blockchain network
  "decimals": 18, // Number of decimals in the token
  "symbol": "EXAMPLE", // Symbol of the base token
  "defaultView": "core", // The default tab to see in your space
  "address": "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2", // The address of the base token
  "token": "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2", // The same address of the base token
  "core": [ // List of official addresses that can post in "Core" tab of your space
    "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7"
  ],
  "min": 123, // Minimum balance to have from the base token to have your proposal visible in the space (unless the address is a core address)
  "invalid": [
    "QmXAZP8tYwX2zZz5EzfxLZUYJt6TM9EmxY1L4qodhZ5zcZ"
  ] // List of proposal ids, use this to remove a proposal from your space
}
```

## **4: Add a logo and space images**

* You must add both `logo.png` and `space.png` images for your space with a size of 256 x 256 pixels.
* The file size should not exceed `50KB`.

## **5: Create a skin \(optional\)**

* If you want the default skin you can delete the file `skin.scss`.
* If you want a skin you can change colors in the file `skin.scss` and change the `.name` to the id of your space. `.name` to `.my-space`

`skin.scss`

```css
.name {
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

## **6: Make a pull request**

* Please name your PR title on the model `Add SYMBOL space`
* It may take 1 or 2 days to get your PR reviewed , merged and appear on Snapshot.

