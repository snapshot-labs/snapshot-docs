---
description: The official JavaScript client for build Snapshot apps.
---

# Snapshot.js

{% embed url="https://github.com/snapshot-labs/snapshot.js" %}

### **Utils**

### **getProvider**

Return a Ethers.js JsonRPCProvider connected to an archive node.

```javascript
import snapshot from '@snapshot-labs/snapshot.js';

const network = '1';
const provider = snapshot.utils.getProvider(network);
```

### **getScores**

Calculate voting power for a list of voters.

```javascript
import snapshot from '@snapshot-labs/snapshot.js';

const space = 'yam.eth';
const strategies = [
  {
    name: 'erc20-balance-of',
    params: {
      address: '0x6B175474E89094C44Da98b954EedeAC495271d0F',
      symbol: 'DAI',
      decimals: 18
    }
  }
];
const network = '1';
const provider = snapshot.utils.getProvider(network);
const voters = [
  '0xa478c2975ab1ea89e8196811f51a7b7ade33eb11',
  '0xeF8305E140ac520225DAf050e2f71d5fBcC543e7',
  '0x1E1A51E25f2816335cA436D65e9Af7694BE232ad'
];
const blockNumber = 11437846;

snapshot.utils.getScores(
  space,
  strategies,
  network,
  provider,
  voters,
  blockNumber
).then(scores => {
  console.log('Scores', scores);
});
```

  


