---
description: Use the categories on the right sidebar or search through the entire FAQ.
---

# FAQs

## Spaces <a id="spaces"></a>



### How can I access my space or the demo space on snapshot?

Snapshot live: `http://snapshot.org/#/<SPACE ENS ADDRESS>`  
Snapshot demo: `http://demo.snapshot.org/#/<SPACE ENS ADDRESS>`

### 

### How can I get my space showing on the Snapshot homepage?

If you already have a space with GitHub see how to Migrate your space to ENS.

{% page-ref page="../spaces/migrate.md" %}

If you want to create a new space with ENS

{% page-ref page="../spaces/create.md" %}



### **What's the difference between admin and authors**

* `Admins` can edit `space settings`
* `Authors` can post `proposals`



## Proposals <a id="proposals"></a>



### Can I edit a proposal once I posted it ?

Nope, you can delete it and make a new one. You can also duplicate it, that will prefill all the fields.



### Why I can't save my proposal ?

* Make sure you filled "Question" and "What is you proposal" placeholders.
* Make sure you've added at least two choices.
* Make sure you've selected a set of actions for voting system, start and end date.
* Make sure to enter a "snapshot block number"

If you still cant's save your proposal contact us on [Discord](http://discord.snapshot.org) or [Telegram](https://t.me/snapshotlabs)



### Can I create different types of proposals like "core" and "community"?

If a proposal is created by an `Author` \(added in `space settings`\) it will be shown as `core` proposal.  
All other proposal are community proposals.



## Votes



### **Why I can't vote?**

To be able to vote you need voting power, your voting power is calculated at the "snapshot" of the proposal. The snapshot is the block number where we read the voting power from. If you didn't have the tokens at this block number, you will not have any voting power and won't be able to vote.



### **I am getting an error "wrong timestamp", what is the problem?**

Most likely the issue is that your computer time is not synchronized with the internet time. This is how to fix this:

**On MacOS**  
On your Mac, choose Apple menu &gt; System Preferences, then click Date & Time.  
Click Date & Time, then set the date and time automatically.

[![MacOS](https://user-images.githubusercontent.com/55286013/135220574-a1c1ff59-e12a-4ba1-b234-6ebed9140f69.png)](https://user-images.githubusercontent.com/55286013/135220574-a1c1ff59-e12a-4ba1-b234-6ebed9140f69.png)

**On Windows**  
Go to Start &gt; Settings &gt; Time & language &gt; Date & time.  
Then set time automatically

[![Windows](https://user-images.githubusercontent.com/55286013/135220660-b6384c2d-a247-44af-ad06-b5429633a74e.png)](https://user-images.githubusercontent.com/55286013/135220660-b6384c2d-a247-44af-ad06-b5429633a74e.png)



## Strategies



### What strategy should I use for my proposal

It widely depends on your use case, if you want coin-voting \(1 token= 1 vote\) you can use "erc20-balance-of", however you may want:

* Delegate voting power using a delegation strategy
* Weighting voting power using a quadratic strategy
* NFT voting with an ERC-721 based strategy
* Only allow certain members to vote using whitelist strategy
* Calculate voting power from multiple chains with multichain strategy

You can combine up to 5 strategies on a single proposal \(combination work as OR not AND opperator\)

At the time of writing snapshot has over 150 voting strategies.   
Explore them here [https://snapshot.org/\#/strategies](https://snapshot.org/#/strategies)  
You can even preview actions using the playground button.



### I have updated my strategy, when the changes will take effect ?

Your changes will only affect future proposals, already existing proposals can not be edited.



### May I use multiple chains / networks strategies in my proposals ?

Yes you can use multi-chain strategy in your space, which can calculate voting power from multiple networks. Check this out: [https://snapshot.org/\#/strategy/multichain](https://snapshot.org/#/strategy/multichain)

## Delegation

## Networks

## Contribution

## API





{% page-ref page="spaces.md" %}

