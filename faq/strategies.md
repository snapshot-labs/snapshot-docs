# Strategies

## I have updated my strategy, when the changes will take effect ?

Once a proposal is created, if you change strategies, it will take effect from next proposal - It will not affect previous proposal.

## May I use multiple chains / networks in my space ?

Yes you can use multichain strategy in your space, which can calculate voting power from multiple networks.

## What is the decimal parameter ?

* When you create a token you have to define the number of decimal that you want
* Most of the token use 18 decimals

## What is the address parameter ?

In order to setup a coin-voting strategy i.e. "erc20-balance-of" you need to change the placeholder address to your own token ERC-20 address.

## Can I deploy my own token on Snapshot

Not yet, you need to create your token on another platform.

## What strategy should I use for my proposal

It's widely depends on your use case, if you want coin-voting \(1 token= 1 vote\) you can use "erc20-balance-of", however you may want:

* Delegate voting power using a delegation strategy
* Weighting voting power using a quadratic strategy
* NFT voting with an ERC-721 based strategy

At the time of writing snapshot has over 150 voting strategies that you can combine. Explore them here [https://snapshot.org/\#/strategies](https://snapshot.org/#/strategies)   
You can even preview actions using the playground button.

