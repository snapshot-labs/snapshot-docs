---
description: >-
  The official JavaScript client for implementing Snapshot's functionality in
  other apps.
---

# Snapshot.js

## **Overview**

**`Snapshot.js`** is an open source JavaScript client which comes with the core functions of the Snapshot's off-chain voting system. It was designed to work both in the browser and with `Node.js`.

:point\_right: [**Snapshot.js Repository**](https://github.com/snapshot-labs/snapshot.js)



## Get started

### **Installation**

**Node.js**

To install Snapshot.js on Node.js, open your terminal and run:

```shell
npm i @snapshot-labs/snapshot.js
```

**Browser**

You can create an index.html file and include Snapshot.js with:

```html
<script src="https://cdn.jsdelivr.net/npm/@snapshot-labs/snapshot.js"></script>
```

### Development

**Install dependencies**

```shell
yarn
```

**Build package**

```shell
yarn build
```

## Usage

#### Base features

#### Init client

```javascript
import snapshot from '@snapshot-labs/snapshot.js';

const hub = 'https://hub.snapshot.org'; // or https://testnet.hub.snapshot.org for testnet
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
  reason: 'Choice 1 make lot of sense',
  app: 'my-app'
});
```

#### Create proposal

```javascript
import { Web3Provider } from '@ethersproject/providers';

const web3 = new Web3Provider(window.ethereum);
const [account] = await web3.listAccounts();

const receipt = await client.proposal(web3, account, {
  space: 'yam.eth',
  type: 'single-choice', // define the voting system
  title: 'Test proposal using Snapshot.js',
  body: 'This is the content of the proposal',
  choices: ['Alice', 'Bob', 'Carol'],
  start: 1636984800,
  end: 1637244000,
  snapshot: 13620822,
  plugins: JSON.stringify({}),
  app: 'my-app' // provide the name of your project which is using this snapshot.js integration
});
```

#### **Create or edit a space**

```javascript
import { Web3Provider } from '@ethersproject/providers';

const web3 = new Web3Provider(window.ethereum);
const [account] = await web3.listAccounts();

const receipt = await client.space(web3, account, {
  "space":"pistachiodao.eth",
  "settings": `{
    "name":"pistachiodao.eth",
    "avatar":"", // IPFS address of space avatar
    "about":"",
    "network":"1",
    "symbol":"XYZ",
    "website": "",
    "twitter": "",
    "github": "",
    "coingecko": "",
    "domain":"", // custom domain address
    "skin":"", // custom skin when custom domain is set
    "guidelines":"", // guidelines for proposal creation
    "template":"", // template for new proposals
    "private": false, // visibility in the space list
    "moderators":[], //  list of space Moderators
    "members": [], // list of Authors
    "admins":[],
    "categories":[
      "social",
      "media"
    ],
    "plugins":{
      "hal":{}
    },
    "parent":"", // main space ID
    "children":[], // list of sub-spaces
    "voting": {
      "delay":0, // voting delay in seconds
      "hideAbstain":false,
      "period":0, // voting duration in seconds
      "quorum":0,
      "type":"", // define the default voting system
      "privacy":"" // pass "shutter" for shielded voting
    },
    "strategies":[{
      "name":"ticket",
      "network":"1",
      "params":{"symbol":"TICKET"}
    }], // provide up to 8 strategies with their configuration
    "validation":{
      "name":"basic",
      "params":{}
    }, // provide one proposal validation strategy
    "filters":{
      "onlyMembers": false // enable Authors only to create proposals
    }, 
    "voteValidation":{
      "name":"any",
      "params":{}
    }, // provide one voting validation strategy
    "treasuries":[] // provide the organization's treasury account(s)
    }`
});
```

#### Join a space

```javascript
import { Web3Provider } from '@ethersproject/providers';

const web3 = new Web3Provider(window.ethereum);
const [account] = await web3.listAccounts();

const receipt = await client.follow(web3, account, {
  "space":"pistachiodao.eth"
});
```

### **Utils**

{% hint style="info" %}
The below methods are sending a request to Score API. Same as [Hub API](api/) it requires an API Key for **higher usage limits**. You can see we require it for the **`apiKey`** variable.\
\
If you already have an API Key for Hub API, you can reuse it for Score. \
In case you don't have an API Key, follow the instructions here: [api-keys.md](api/api-keys.md "mention")
{% endhint %}

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
const snapshot = 11437846;
const apiKey = 'your_api_key_here' // get an API Key for higher limits
const url = `https://score.snapshot.org/?apiKey=${apiKey}`

snapshot.utils.getScores(
  space,
  strategies,
  network,
  voters,
  snapshot,
  url
).then(scores => {
  console.log('Scores', scores);
});
```

#### getVp

Retrieve voting power for a specific address using given strategies.

```javascript
import snapshot from '@snapshot-labs/snapshot.js';

const address = '0xa478c2975ab1ea89e8196811f51a7b7ade33eb11';
const network = '1';
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
const snapshot = 11437846;
const space = 'yam.eth';
const delegation = false;
const apiKey = 'your_api_key_here' // get an API Key for higher limits
const options = { url: `https://score.snapshot.org/?apiKey=${apiKey}` }

snapshot.utils.getVp(address, network, strategies, snapshot, space, delegation, options).then(vp => {
  console.log('Voting Power', vp);
});
js
```

#### validate

Validate an address using a given validation strategy.

```javascript
import snapshot from '@snapshot-labs/snapshot.js';

const validationName = 'basic';
const author = '0xa478c2975ab1ea89e8196811f51a7b7ade33eb11';
const spaceId = 'yam.eth';
const networkId = '1';
const snapshot = 11437846;
const validationParams = {
  minScore: 100
};
const options = {};
const apiKey = 'your_api_key_here' // get an API Key for higher limits
const url = `https://score.snapshot.org/?apiKey=${apiKey}`

snapshot.utils.validate(validationStrategyName, author, spaceId, networkId, snapshot, validationParams, options, url).then(result => {
  console.log('Validation Result', result);
});

```

#### **getProvider**

Return a Ethers.js JsonRPCProvider connected to an archive node.

```javascript
import snapshot from '@snapshot-labs/snapshot.js';

const network = '1';
const provider = snapshot.utils.getProvider(network);
```

