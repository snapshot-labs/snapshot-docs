---
description: Create your own space on Snapshot!
---

# Create a space \(on GitHub\)

### **1: Fork Snapshot spaces repository here**

{% embed url="https://github.com/bonustrack/snapshot-spaces" caption="" %}

{% hint style="info" %}
**Update your fork with the original repo using Git**

If you have already forked a space, you must update your repo before submitting changes.

Use the 4 commands below to sync your forked repository with the original repository.
{% endhint %}

```text
git remote add master https://github.com/snapshot-labs/snapshot-spaces.git
git fetch master
git checkout master
git merge master/master
```

### **2: Copy the space "example" folder**

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

### **3: Space metadata**

Note that your path folder name will be the name that will show on the snapshot link:

* https://snapshot.page/\#/**your-space**

Example: `index.json`

```javascript
{
  "name": "Your Space", // Name of your space (max 20 chars)
  "network": "1", // What network you are on? (if on Ethereum it is "1", for other check: https://docs.snapshot.page/networks)
  "symbol": "SYMBOL", // Your main token symbol 
  "skin": "your-space", // Copy skin filename "example.scss" located at "/skins" folder and renaming it to "your-space.scss"
  "domain": "vote.yourdomain.com", // Add your voting/governance subdomain if you have one
  "strategies": [ // Strategies
    {
      "name": "erc20-balance-of", // Strategy name
      "params": { // Strategy parameters
        "address": "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2", // Address of the base token
        "symbol": "SYMBOL", // Symbol of the base token
        "decimals": 18 // Decimals of the base token
      }
    }
  ],
  "members": [ // List of official addresses that can post in "Core" tab of the space
    "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7" // Core member address
  ],
  "filters": { // Filters
    "defaultTab": "all", // The default tab for the space
    "minScore": 123, // Minimum balance from the base token that a user should have to show his proposal in the space (unless the address is a core address)
    "onlyMembers": true // Shows only core tab and core proposals
    "invalids": [ // List of proposals IDs (use this to remove a proposal from your space)
      "QmXAZP8tYwX2zZz5EzfxLZUYJt6TM9EmxY1L4qodhZ5zcZ",
      "QmXAZV8tYwX2zZz5EzfxLZUYJt6TM9EmxY1L4qodhZ5lbL"
    ]
  }
}
```

#### **R**equired **fields:** `token, name, network, symbol, strategies`

### **4: Add a logo and space images**

1. You must add both `logo.png` and `space.png` images for your space with a size of 256 x 256 pixels.
2. The file size should not exceed `50KB`.

### **5: Create a skin \(optional\)**

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

### **6: Make sure everything is ready**

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

### **7: Make a pull request**

* Please name your PR title on the model `Add SYMBOL space`
* It may take 1 or 2 days to get your PR reviewed, merged and appear on Snapshot.

