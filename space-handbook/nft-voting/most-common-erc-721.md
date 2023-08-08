---
description: Learn which strategies to use to allow users holding NFTs to get Voting power.
---

# Most common: ERC-721

[ERC-721](https://eips.ethereum.org/EIPS/eip-721) was the first standardized interface for creating and trading NFTs and is still considered the gold standard.&#x20;

ADD SOME JOYFUL TEXT HERE

In Snapshot, the `balanceOf` method is applied to both the **erc721** and **erc20** strategies. The main difference in their implementation is that the decimal of an NFT should always be set to **0**.&#x20;

{% hint style="info" %}
All NFTs strategies can be combined with other Voting strategies, like for example `erc20-balance-of` or `whitelist`. The results of each Strategy are summed up to result in the final Voting power of each user.
{% endhint %}

### [erc721](https://snapshot.org/#/strategy/erc721)

This strategy returns the balance of the specific ERC721 NFT that the user holds.&#x20;

It's the **most common strategy** for NFT-based voting.&#x20;

How to set it up? Just provide the contract address of the NFT and its symbol.

One who owned the specified NFT at the snapshot of proposal creation will be able to vote based on the number of NFTs they have in their wallet.&#x20;

{% hint style="info" %}
If your project is releasing the NFT collection in batches with a limited amount of NFT minted on the deployment of the contract, then don't worry.&#x20;

It won't affect the calculation of the Voting power. Feel free to implement it in your space and engage your community in the governance process! ⚡️
{% endhint %}

**Strategy setup:**

```json
{
  "address": "0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB",
  "symbol": "PUNK"
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/erc721" %}

### [erc721-with-multiplier](https://snapshot.org/#/strategy/erc721-with-multiplier)

This strategy gives an arbitrary weight to the balance of the voters for a specific ERC721 NFT.

By adjusting the `multiplier` to 100, if a user owns 1 LAND in his wallet, he will get 100 votes (1\*100) on the proposal.

**Strategy setup:**

```json
{
  "address": "0xf87e31492faf9a91b02ee0deaad50d51d56d5d4d",
  "symbol": "LAND",
  "multiplier": 100
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/erc721-with-multiplier?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4Zjg3ZTMxNDkyZmFmOWE5MWIwMmVlMGRlYWFkNTBkNTFkNTZkNWQ0ZCIsInN5bWJvbCI6IkxBTkQiLCJtdWx0aXBsaWVyIjoyMDAwfSwibmV0d29yayI6IjEiLCJzbmFwc2hvdCI6IiIsImFkZHJlc3NlcyI6WyIweDRlYWM2MzI1ZTFkYmYxYWM5MDQzNGQzOTc2NmUxNjRkY2E3MTEzOWUiLCIweDFiMjA0NDI0NTYzZGNmY2FiZDJhZWU2MzIxNjNiOWU2ZGM4YmQ0ZjMiXX0." %}

### [erc721-with-tokenid](https://snapshot.org/#/strategy/erc721-with-tokenid)

Each NFT under the same contract address can be identified by its unique `tokenID`.

This strategy returns the balance of the voters for a specific ERC721 NFT with a given `tokenID`.

If a user holds the NFT which tokenID is included in the `tokenIds` parameter, they will get **1 vote** regardless of how many they hold in total.

**Strategy setup:**

```json
{
  "address": "0x22C1f6050E56d2876009903609a2cC3fEf83B415",
  "symbol": "POAP",
  "tokenIds": ["613607", "613237"]
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/erc721-with-tokenid?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4MjJDMWY2MDUwRTU2ZDI4NzYwMDk5MDM2MDlhMmNDM2ZFZjgzQjQxNSIsInN5bWJvbCI6IlBPQVAiLCJ0b2tlbklkcyI6WyI2MTM2MDciLCI2MTMyMzciXX0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHgyYjg1MDc1NzAyYjViYzQ3MzdkOGUxNTYwYjdlZmU4NTM1MTA1YjQ3IiwiMHgzZTE3ZmFjOTUzZGUyY2Q3MjliMGFjZTdmNmQ0MzUzMzg3NzE3ZTllIiwiMHhFNzZCZTlDMWUxMDkxMGQ2QmM2YjYzRDgwMzE3Mjk3NDc5MTBjMmY2IiwiMHhDNWUxNTY5NzcyYjJkNDI1QWM5NDY5ZDM5RjE3MzQxQzAxZTFDRjRjIl19" %}

### [erc721-with-tokenid-weighted](https://snapshot.org/#/strategy/erc721-with-tokenid-weighted)

This strategy is a modification of [erc721-with-tokenid](most-common-erc-721.md#erc721-with-tokenid).&#x20;

It allows **1 vote per whitelisted tokenID** specified in the parameter.

So in contrary to the previous strategy, the user who holds **three NFTs**, each included in the strategy setup, will have **3 Voting power**.

**Strategy setup:**

```json
{
  "address": "0x30cDAc3871c41a63767247C8D1a2dE59f5714e78",
  "symbol": "Reaper(s)",
  "tokenIds": ["2112", "2871", "3221", "3587"]
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/erc721-with-tokenid-weighted?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4MzBjREFjMzg3MWM0MWE2Mzc2NzI0N0M4RDFhMmRFNTlmNTcxNGU3OCIsInN5bWJvbCI6IlJlYXBlcihzKSIsInRva2VuSWRzIjpbIjIxMTIiLCIyODcxIiwiMzIyMSIsIjM1ODciXX0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIxNzUzNjA0NCIsImFkZHJlc3NlcyI6WyIweDg2MzM3OUFiNDAxZDQ1NDgzNEUxRkUyZUNlNDhGNTFhMjllRTlkN0EiLCIweDRDNEU2ZjEzZmI1RTNmNzBDMzc2MDI2MmEwM0UzMTc5ODI2OTFkMTAiLCIweGY1ODE5NWRlM2FmOTFhZmYxZjhkZDU1OWFkNDFmODhmMWI2YzRhYWYiXX0." %}

### [erc721-with-tokenid-range-weights](https://snapshot.org/#/strategy/erc721-with-tokenid-range-weights)

The strategy returns the weighted balance of the voters for ERC721 NFT of which the Token ID is specified in the `tokenIdWeightRanges`.

**Why it might be useful for your space?**

* NFTs in the collection have **continuous** `tokenIDs`
* You want to **assign different weights** to specific batches of the collection (higher VP for first NFT minters, lower VP for latest NFT owners)

The NFT can be assigned a **different weight** based on the range its token ID falls within.

{% hint style="info" %}
If it doesn't fit into any range, it'll still be counted as 1 by `defaultWeight` setting. However, If you don't want to include the NFT that's **outside of the range** into voting power, simply set that `defaultWeight` to 0. &#x20;
{% endhint %}

For example, a user who owns 3 NFTs with the tokenIds: `1000`, `6000` and `8000` respectively will have **3** Voting power. \[(1\*2)+(1\*1)+(1\*0)]

**Strategy setup:**

```json
{
  "address": "0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d",
  "symbol": "BAYC",
  "defaultWeight": 0,
  "tokenIdWeightRanges": [
    { "start": 0, "end": 1000, "weight": 2 },
    { "start": 1001, "end": 6000, "weight": 1 }
  ]
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/erc721-with-tokenid-range-weights?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4MzBjREFjMzg3MWM0MWE2Mzc2NzI0N0M4RDFhMmRFNTlmNTcxNGU3OCIsInN5bWJvbCI6IlJlYXBlcihzKSIsImRlZmF1bHRXZWlnaHQiOjEsInRva2VuSWRXZWlnaHRSYW5nZXMiOlt7InN0YXJ0IjowLCJlbmQiOjMwMDAsIndlaWdodCI6MX0seyJzdGFydCI6MzAwMSwiZW5kIjo0NzE1LCJ3ZWlnaHQiOjJ9XX0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHg4NjMzNzlBYjQwMWQ0NTQ4MzRFMUZFMmVDZTQ4RjUxYTI5ZUU5ZDdBIiwiMHg0QzRFNmYxM2ZiNUUzZjcwQzM3NjAyNjJhMDNFMzE3OTgyNjkxZDEwIiwiMHhmNTgxOTVkZTNhZjkxYWZmMWY4ZGQ1NTlhZDQxZjg4ZjFiNmM0YWFmIl19" %}
