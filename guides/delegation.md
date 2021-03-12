---
description: Snapshot delegation.
---

# Delegation

### Delegation contract

Snapshot use the Gnosis "Delegate Registry" contract here:  
[https://github.com/gnosis/delegate-registry](https://github.com/gnosis/delegate-registry)  
  
The contract is deployed on this address: [0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446](https://etherscan.io/address/0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446#code)  
\(Also available on Rinkeby and Kovan at the same address\)  
  
Delegations are stored on this subgraph:  
[https://thegraph.com/explorer/subgraph/snapshot-labs/snapshot](https://thegraph.com/explorer/subgraph/snapshot-labs/snapshot)

### Delegate voting power

####  From Snapshot interface

1. Go to [https://snapshot.page/\#/delegate](https://snapshot.page/#/delegate).
2. Type in which address you want to delegate to.
3. Type in the space key you want your delegation to take effect on. _\(If no space selected, effect will take place on all spaces\)_
4. Click confirm to save your delegation.

#### With a smart contract

You need to call the method "**setDelegate**" with the space id as first argument \(must be encoded with Keccak\), and the address of the delegate as second argument. 



