# Block Number

Block number is important, to lock the state of community members who are able to vote. Meaning that if you attempt to vote on a proposal and block number is in the past, and you weren't holding required token yet, your vote will not be counted.

Explained in depth:

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

