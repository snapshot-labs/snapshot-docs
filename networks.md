# Networks

Snapshot supports EVM-based networks. All the networks currently supported are visible here: [https://snapshot.org/#/?type=networks](https://snapshot.org/#/?type=networks)

### Add a new network

* Make a pull request on this file:\
  [https://github.com/snapshot-labs/snapshot.js/blob/master/src/networks.json](https://github.com/snapshot-labs/snapshot.js/blob/master/src/networks.json)\
  Make sure the RPC node is an archive node, this is mandatory. Snapshot uses archive nodes to calculate voting power at a specific block time. You will also need to add a [multicall contract](https://github.com/makerdao/multicall/blob/master/src/Multicall.sol) address. Make sure to update `logo` parameter with an IPFS file.

