# Create a proposal

1. Go to a project's space
2. Click on “Connect wallet” button in top right corner 
3. Connect with wallet provider where you hold relevant token
4. Click on “New proposal” button at the project homepage
5. Fill out the Title in accordance with project naming standard
6. Fill out the large text field with your community proposal
7. Select the desired voting options 
8. Now go to the “Actions” box 
9. Select the start date 
10. Select the end date \(allow enough time for voting\)
11. Fill out the Snapshot block number \(further detail below\)

#### **Snapshot block number**

This number is important to lock the state of community members who are able to vote.

Meaning that if you attempt to vote on a proposal and block number is in the past, and you weren't holding required token yet, your vote will not be counted.

`H = h + ((t1 — t0) / a)`

Where:

* `H` = target block height
* `h` = current block height
* `t0` = current timestamp \(in seconds\)
* `t1` = target timestamp \(in seconds\)
* `a` = average time to solve a block \(in seconds\)

Or...

`last_block_number + ((future_time - time_now) / block_time)`

So, for example, using a [current epoch time](https://www.epochconverter.com) of 1481214124, the epoch time of 1482537600 for midnight Christmas Eve, and the last block of 2771338:

`2771338 + ((1482537600 - 1481214124) / 14) = 2865872`

Or just look at [etherscan.io/blocks](https://etherscan.io/blocks) and use the last block number.

_How to use Snapshot as proposal creator continued:_

1. Click on “Publish” and create the proposal 
2. Sign the message via your wallet and you are done

