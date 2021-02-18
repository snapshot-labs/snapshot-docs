---
description: Create a strategy and use it on your own space.
---

# Create new strategy

To add your own strategy on Snapshot you need to fork the **snapshot.js** repository and create pull request.

{% embed url="https://github.com/snapshot-labs/snapshot.js" caption="Snapshot.js repository" %}

#### 1. Navigate to the **`src\strategies`**

```bash
└── src
    └── strategies
        └── erc20-balance-of
```

#### 2. Create a copy of the **`erc20-balance-of`** strategy folder and rename it to the name of your strategy

#### 3. Write the logic of your strategy and test it with:

```javascript
npm run test --strategy=<STRATEGY NAME> // replace <STRATEGY NAME>

// OR

npm run test // for the default strategy
```

#### 4. Include it at**`src\strategies\index.ts` and create a pull request**



