---
description: Create your own space on Snapshot!
---

# Create a space

## **1: Fork Snapshot spaces repository here**

{% embed url="https://github.com/bonustrack/snapshot-spaces" caption="" %}

## **2: Copy the space "example" folder**

{% embed url="https://github.com/bonustrack/snapshot-spaces/tree/master/spaces/example" caption="" %}

```text
|-- spaces
    |-- example
        |-- index.json
        |-- logo.png
        |-- space.png
|-- skins (optional)
    |-- example.scss (optional)
```

## **3: Change your space metadata**

* The name of the folder must be the key of your space.
* This key also corresponds to the slug url and must not be composed with uppercase characters. `"key": "example"` to `"key": "your-space"`

Example: `index.json`

```javascript
{
  "name": "Your Space", // Name of the space (max 12 chars)
  "chainId": 1, // ID of the blockchain network
  "decimals": 18, // Number of decimals in the token
  "symbol": "YOURSPACE", // Symbol of the base token
  "skin": "your-space", // Copy skin filename "example.scss" located at "/skins" folder and renaming it to "your-space.scss"
  "defaultView": "core", // The default tab to see in your space
  "token": "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2", // The same address of the base token
  "core": [ // List of official addresses that can post in "Core" tab of your space
    "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7"
  ],
  "min": 123, // Minimum balance to have from the base token to have your proposal visible in the space (unless the address is a core address)
  "invalid": [ // List of proposal ids, use this to remove a proposal from your space
    "QmXAZP8tYwX2zZz5EzfxLZUYJt6TM9EmxY1L4qodhZ5zcZ"
  ]
}
```

## **4: Add a logo and space images**

1. You must add both `logo.png` and `space.png` images for your space with a size of 256 x 256 pixels.
2. The file size should not exceed `50KB`.

## **5: Create a skin \(optional\)**

1. To create your own skin go to the `/skins` folder.
2. Copy `example.scss` change the name to what you like \(prefferably your space name\).
3. Change the colors, then make sure both the `scss` file and its class name are the same.
4. Exampe: your file is `your-space.scss` class name should be `.your-space`
5. Include your skin name in the `index.json` file as: `"skin": "your-space"`
6. Save it in `/skins` folder.

Example: `your-space.scss`

```css
.your-space {
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

## **6: Make sure everything is ready**

Your files should something like this:

```text
|-- spaces
    |-- your-space
        |-- index.json
        |-- logo.png
        |-- space.png
|-- skins (optional)
    |-- your-space.scss (optional)
```

## **7: Make a pull request**

* Please name your PR title on the model `Add SYMBOL space`
* It may take 1 or 2 days to get your PR reviewed, merged and appear on Snapshot.

