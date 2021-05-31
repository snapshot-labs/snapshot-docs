# Networks

Snapshot support EVM based networks. All the networks currently supported are visible here: [https://snapshot.page/\#/networks](https://snapshot.page/#/networks)

### Add a new network

* Make a pull request on this file: [https://github.com/snapshot-labs/snapshot.js/blob/master/src/networks.json](https://github.com/snapshot-labs/snapshot.js/blob/master/src/networks.json) Make sure the RPC node is an archive node, this is mandatory. Snapshot use archive nodes to calculate voting power at a specific block time. 
* You will also need to add a multicall contract for the newly added network here: [https://github.com/snapshot-labs/snapshot.js/blob/master/src/utils.ts\#L19](https://github.com/snapshot-labs/snapshot.js/blob/master/src/utils.ts#L19)
* And add an image of the network on this folder: [https://github.com/snapshot-labs/snapshot.js/tree/master/src/networks](https://github.com/snapshot-labs/snapshot.js/tree/master/src/networks)



