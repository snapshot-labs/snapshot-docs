---
description: Create a strategy and use it on your own space
---

# Create a new strategy

To add your own strategy on Snapshot you need to fork the **snapshot-strategies** repository and create a pull request.

{% embed url="https://github.com/snapshot-labs/snapshot-strategies" %}

### 1. Navigate to the **`src\strategies`**

```bash
└── src
    └── strategies
        └── erc20-balance-of
```

### 2. Create a copy of the **`erc20-balance-of`** strategy folder and rename it to the name of your strategy

### 3. Write the logic of your strategy, include it in\*\*`src\strategies\index.ts` and test it with:

```javascript
npm run test --strategy=<STRATEGY NAME> // replace <STRATEGY NAME>
```

See [How to write a basic strategy](how-to-write-a-basic-strategy.md)

### 4. Make sure you pass the checklist

Have a look here on the requirements for adding a new strategy and make sure you full fill the points in the checklist: [https://github.com/snapshot-labs/snapshot.js/issues/212](https://github.com/snapshot-labs/snapshot.js/issues/212)

### 5. Create a pull request

The team will then review your PR and after it's approved and merged it will be available in your space settings.
