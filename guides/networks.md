---
description: >-
  This page explains which networks are supported by Snapshot and how to add a
  new one.
---

# Networks

## EVM-based networks

Snapshot supports EVM-based networks. You can explore them at **** [**https://snapshot.org**](https://snapshot.org) by selecting the `Networks` filter:

<figure><img src="../.gitbook/assets/image (7) (3).png" alt=""><figcaption></figcaption></figure>

You can also follow this link directly: [**https://snapshot.org/#/?type=networks**](https://snapshot.org/#/?type=networks).

## Add a new network

If you can't see the network you are looking for on the list or you want to add your custom network, follow the steps below to include it within Snapshot.

#### Requirements

* New network must be **EVM**-based
* RPC node must be an **archive node**
* RPC node's url must use ** `https` **&#x20;
* Multicall contract must be **verified and published**&#x20;
* Logo has to be stored on **IPFS**

### 1. Fork the repository

Create a fork of the [**snapshot.js**](https://github.com/snapshot-labs/snapshot.js) repository.

### 2. Prepare the network details

Update the **** [**network.json**](https://github.com/snapshot-labs/snapshot.js/blob/master/src/networks.json) file with a new JSON object storing information about the new network, following the example below:

```json
  "30": {
    "key": "30",
    "name": "RSK Mainnet",
    "chainId": 30,
    "network": "rsk mainnet",
    "multicall": "0x4eeebb5580769ba6d26bfd07be636300076d1831",
    "rpc": [
      "https://public-node.rsk.co" # make sure the RPC node url is using https protocol
    ],
    "explorer": {
      "url": "https://explorer.rsk.co"
    },
    "start": 2516442, # specify the number of the first block
    "logo": "ipfs://QmXTwpE1SqoNZmyY4c3fYWy6qUgQELsyWKbgJo2Pg6K6V9" 
  }
```

### 3. Check if the network is set correctly

Head to **** [**https://snapshot-networks.on.fleek.co/**](https://snapshot-networks.on.fleek.co/) **** to test if your network is reachable:

a. Click the first network from the left sidebar and click `Edit networks.json` on the right side:

<figure><img src="../.gitbook/assets/image (1) (4).png" alt=""><figcaption></figcaption></figure>

b. Add the JSON object with your network details (be careful with typos!) and click `Apply`. **Do not refresh the page!**

<figure><img src="../.gitbook/assets/image (3) (4).png" alt=""><figcaption></figcaption></figure>

c. Search for your network in the left sidebar. You can look for the `chainId` or the network's `name`

d. Scroll up to the top of the page and check if:

* it is a Full Archive node
* the last block is fetched correctly (click on it to see its timestamp)
* there are no errors

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

### 4. Create a Pull Request

If everything works correctly create a new PR on the original [snapshot.js](https://github.com/snapshot-labs/snapshot.js/) repo.

### 5. Wait for the team to approve the PR

It's now in the hands of the Snapshot team to review your changes and apply them to [https://snapshot.org](https://snapshot.org).&#x20;

The average time to merge a PR is 2-3 days, so please be patient! 😉
