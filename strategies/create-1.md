---
description: Create a voting validation strategy and use it in your own space
---

# Create a new voting validation

To add your own voting validation strategy on Snapshot you need to fork the **snapshot-strategies** repository and create a pull request.

{% embed url="https://github.com/snapshot-labs/snapshot-strategies" %}

### 1. Navigate to the **`src\validations.`**

```bash
└── src
    └── validations
        └── basic
```

### 2. Create a copy of the **`basic`** strategy folder and rename it to the name of your voting validation.

### 3. Customize the logic of your voting validation.

If you are not sure about the `Validation` class, have a look at its definition:

{% embed url="https://github.com/snapshot-labs/snapshot-strategies/blob/master/src/validations/validation.ts" %}

The validation name has to be included in the[ `index.ts`](https://github.com/snapshot-labs/snapshot-strategies/blob/master/src/validations/index.ts)  in the `validationClasses` variable.

### 4. Test your validation

To make sure your validation passes all tests, run:

```javascript
npm run test --validation=<VALIDATION NAME> // replace <VALIDATION NAME>
```

### 4. Make sure you pass the checklist

Have a look here on the requirements for adding a new validation strategy and make sure you full fill the points in the checklist:&#x20;

[https://github.com/snapshot-labs/snapshot-strategies#checklist-for-adding-a-new-strategy](https://github.com/snapshot-labs/snapshot-strategies#checklist-for-adding-a-new-strategy)

### 5. Create a pull request

The team will then review your PR and after it's approved and merged it will be available to chose in your space settings.
