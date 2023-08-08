---
description: The standard for fungible, non-fungible, and semi-fungible tokens.
---

# Multi-token: ERC-1155

Let's start with a quick overview of the [ERC721](https://eips.ethereum.org/EIPS/eip-721) and [ERC1155](https://ethereum.org/pl/developers/docs/standards/tokens/erc-1155/) standards:

|              | Pros                                                                            | Cons                                                                           |
| ------------ | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **ERC-721**  | **Most widely recognized**, golden NFT standard                                 | Inability to conduct **batch** transfers                                       |
| **ERC-1155** | Supports **different token types in a single contract**, allows batch transfers | Stores **less robust information** in order to save time and transaction costs |

Let's have a look at what Voting strategies you can use in your space:

### [erc1155-balance-of](https://snapshot.org/#/strategy/erc1155-balance-of)

The strategy returns the balance of a **specific** ERC-1155 token in the user's wallet.

Since the ERC-1155 standard supports multiple token types, the `tokenId` here may refer to a particular kind of token or a single item of the collection under the contract address.

{% hint style="info" %}
If you want to get the balance of all tokenIds in the contract, you can use the `erc1155-balance-of-all` strategy. If you have multiple tokenIds, you can use the `erc1155-balance-of-ids` or `erc1155-balance-of-ids-weighted` strategy.
{% endhint %}

**Strategy setup:**

```json
{
  "symbol": "ABC",
  "address": "0xE18a32192ED95b0FE9D70D19e5025f103475d7BA",
  "tokenId": "0x8000000000000000000000000000000200000000000000000000000000000000",
  "decimals": 0
}
```

You can test it out in the **Playground on Snapshot**:

{% embed url="https://snapshot.org/#/playground/erc1155-balance-of?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiQUJDIiwiYWRkcmVzcyI6IjB4RTE4YTMyMTkyRUQ5NWIwRkU5RDcwRDE5ZTUwMjVmMTAzNDc1ZDdCQSIsInRva2VuSWQiOiIweDgwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAyMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAiLCJkZWNpbWFscyI6MH0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHgwQjcwNTZlMkQ5MDY0ZjJlYzg2NDdGMWFlNTU2QkFjYzA2ZGE2RGI0IiwiMHhjYzVEZGM4Q0NENUIxRTkwQmM0MkY5OThlYzg2NEVhZDAwOTBBMTJCIiwiMHgwMTU0ZDI1MTIwRWQyMEE1MTZmRTQzOTkxNzAyZTc0NjNjNUE2RjZlIl19" %}

### [erc1155-all-balances-of](https://snapshot.org/#/strategy/erc1155-all-balances-of)

This strategy returns the balance of voters for **all tokens** in an ERC1155 contract.

{% hint style="warning" %}
On **Polygon**, works only with contracts with total tokenIds less than 6000.
{% endhint %}

**Strategy setup:**

```
{
  "address": "0x61fcE80D72363B731425c3A2A46a1A5fed9814B2",
  "symbol": "CYBORG"
}
```

You can test it out in the **Playground on Snapshot:**

{% embed url="https://snapshot.org/#/playground/erc1155-all-balances-of?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4NzFlYjVjMTc5Y2ViNjQwMTYwODUzMTQ0Y2JiOGRmNWJkMjRhYjVjYyIsInN5bWJvbCI6IkNPUkdJIn0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHgwNjY1OEZkNzAwMjNmNTI3QkZBYzFBNmQ5MTQxQzU2ZDk5YzY1MTI5Il19" %}

### [erc1155-balance-of-ids](https://snapshot.org/#/strategy/erc1155-balance-of-ids)

Use this strategy if you want to calculate the Voting power taking into account **multiple tokenIDs.**

{% hint style="danger" %}
Try using this strategy with only a few tokenIDs passed in the parameter for the Score API server is likely to have difficulty handling a large number of requests.
{% endhint %}

**Strategy setup:**

```json
{
  "symbol": "ABC",
  "address": "0x2939b94BDc377e66A377cfc15028DF3Bd6aC6C28",
  "ids": [
    "59",
    "352"
  ]
}
```

You can test it out in the **Playground on Snapshot:**

{% embed url="https://snapshot.org/#/playground/erc1155-balance-of-ids?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiQUJDIiwiYWRkcmVzcyI6IjB4Mjg0NzJhNThBNDkwYzVlMDlBMjM4ODQ3RjY2QTY4YTQ3Y0M3NmYwZiIsImlkcyI6WyIwIl19LCJuZXR3b3JrIjoiMSIsInNuYXBzaG90IjoiIiwiYWRkcmVzc2VzIjpbIjB4MzQ1MThmNTU1OTQyNWE3YmIwNmY2NjE5NjkyMGFmMTBlMTkzOGI1ZiJdfQ.." %}

### [erc1155-with-multiplier](https://snapshot.org/#/strategy/erc1155-with-multiplier)

The equivalent of the [#erc721-with-multiplier](most-common-erc-721.md#erc721-with-multiplier "mention")Voting strategy.

By adjusting the `multiplier` to 5, if a user owns 1 DAWN in his wallet, they will get **5 Voting power** (1\*5).

**Strategy setup:**

```json
{
  "address": "0x2C56b43983Ca77cc29b27B4a731F0f0d54ae7e52",
  "tokenId": 1,
  "symbol": "DAWN",
  "decimals": 0,
  "multiplier": 5
}
```

You can test it out in the **Playground on Snapshot:**

{% embed url="https://snapshot.org/#/playground/erc1155-with-multiplier?query=eyJwYXJhbXMiOnsiYWRkcmVzcyI6IjB4MkM1NmI0Mzk4M0NhNzdjYzI5YjI3QjRhNzMxRjBmMGQ1NGFlN2U1MiIsInRva2VuSWQiOjEsInN5bWJvbCI6IkRBV04iLCJkZWNpbWFscyI6MCwibXVsdGlwbGllciI6NX0sIm5ldHdvcmsiOiI0Iiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHg5Y0E3MEI5M0NhRTU1NzY2NDVGNUYwNjk1MjRBOUI5YzNhZWY1MDA2IiwiMHhiNWFFNTE2OUY0RDc1MGU4MDI4ODRkODFiNGY5ZUM2NmM1MjUzOTZGIl19" %}

### [erc1155-balance-of-ids-weighted](https://snapshot.org/#/strategy/erc1155-balance-of-ids-weighted)

If you'd like to give more or less weight to a list of specific tokenIDs, you can do so by using this strategy. It might serve as a great addition to the [#erc1155-with-multiplier](multi-token-erc-1155.md#erc1155-with-multiplier "mention") for VP differentiation.

**Strategy setup:**

```json
{
  "symbol": "ABC",
  "address": "0x28472a58A490c5e09A238847F66A68a47cC76f0f",
  "ids": [
    "0",
    "1"
  ],
  "weight": 10
}
```

You can test it out in the **Playground on Snapshot:**

{% embed url="https://snapshot.org/#/playground/erc1155-balance-of-ids-weighted?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiQkFMIiwiYWRkcmVzcyI6IjB4YmExMDAwMDA2MjVhMzc1NDQyMzk3OGE2MGM5MzE3YzU4YTQyNGUzRCIsImRlY2ltYWxzIjoxOH0sIm5ldHdvcmsiOiIxIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHgzNDUxOGY1NTU5NDI1YTdiYjA2ZjY2MTk2OTIwYWYxMGUxOTM4YjVmIl19" %}
