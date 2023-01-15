---
description: Create a strategy and use it on your own space
---

# Create a voting strategy

To add your own voting strategy on Snapshot you need to fork the **snapshot-strategies** repository and create a pull request.

{% embed url="https://github.com/snapshot-labs/snapshot-strategies" %}

**1. Copy the `erc20-balance-of` strategy folder**&#x20;

Rename the folder to the name of your strategy.

```bash
└── src
    └── strategies
        └── erc20-balance-of
```

**2. Write the logic of your strategy**

Include your strategy in `src\strategies\index.ts` and test it with:

```javascript
npm run test --strategy=<STRATEGY NAME> // replace <STRATEGY NAME>
```

**3. Pass the checklist**

Ensure you meet the requirements for adding a new strategy by reviewing the checklist for adding a new strategy: [https://github.com/snapshot-labs/snapshot-strategies#checklist-for-adding-a-new-strategy](https://github.com/snapshot-labs/snapshot-strategies#checklist-for-adding-a-new-strategy)

**4. Create a pull request**

The team will then review your PR and after it's approved and merged it will be available in your space settings.
