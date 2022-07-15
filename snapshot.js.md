---
description: The official JavaScript client for build Snapshot apps.
---

# Snapshot.js

### **Overview**

{% embed url="https://github.com/snapshot-labs/snapshot.js" %}

#### Init client

```javascript
import snapshot from '@snapshot-labs/snapshot.js';

const hub = 'https://hub.snapshot.org'; // or https://testnet.snapshot.org for testnet
const client = new snapshot.Client712(hub);
```

#### Cast a vote

```javascript
import { Web3Provider } from '@ethersproject/providers';

const web3 = new Web3Provider(window.ethereum);
const [account] = await web3.listAccounts();

const receipt = await client.vote(web3, account, {
  space: 'yam.eth',
  proposal: '0x21ea31e896ec5b5a49a3653e51e787ee834aaf953263144ab936ed756f36609f',
  type: 'single-choice',
  choice: 1,
  metadata: JSON.stringify({})
});
```

#### Create proposal

```javascript
import { Web3Provider } from '@ethersproject/providers';

const web3 = new Web3Provider(window.ethereum);
const [account] = await web3.listAccounts();
const now = Math.floor(Date.now() / 1000);

const sendProposal = async () => {

    const receipt = await client.proposal(signer, getAddress(account), {
      space: "yam.eth",
      type: "single-choice",
      title: "Test proposal using Snapshot",
      body: "body",
      discussion: "",
      choices: ['Alice', 'Bob', 'Carol'],
      start: now,
      end: now + 10000,
      snapshot: 11022534,
      plugins: "{}",
    });
    console.log(receipt)
};

sendProposal()
```

#### **Create or edit a space**

...

#### Join a space

...

### **Utils**

#### **getScores**

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
  voters,
  blockNumber
).then(scores => {
  console.log('Scores', scores);
});
```

#### **getProvider**

Return a Ethers.js JsonRPCProvider connected to an archive node.

```javascript
import snapshot from '@snapshot-labs/snapshot.js';

const network = '1';
const provider = snapshot.utils.getProvider(network);
```

**Integrators shortlist**

Integration: \
Boardroom, Decentraland, Pancake, Synthetix, Commonwealth, Guild.xyz\
\
Data aggregation: \
Messari, DeepDAO.

