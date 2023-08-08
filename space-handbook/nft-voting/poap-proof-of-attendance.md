---
description: Take POAPs into account when calculating the individual Voting power.
---

# POAP - Proof of Attendance

POAPs stands for **Proof of Attendance Protocol.** In simple terms, POAPs are like digital badges or tokens that you can earn for attending or participating in certain events, both in-person and online.

Let's say you attend a conference, workshop, or even a virtual event. The organizers of that event can create a unique digital token called a POAP. It serves as proof that someone was present or participated in that specific event. Each token has a unique code or ID that represents their attendance.

{% hint style="info" %}
In technical terms, POAP is a type of ab NFT in **ERC721** standard. It's minted on the **Gnosis chain** and can be migrated to ETH Mainnet as an option.\
\
Its **contract** can be found here: [0x22C1f6050E56d2876009903609a2cC3fEf83B415](https://gnosisscan.io/address/0x22c1f6050e56d2876009903609a2cc3fef83b415).

Every single POAP has a unique **tokenID**.&#x20;
{% endhint %}

Now, how can you reward your community for their attendance by giving them Voting power?

There are several strategies that you can use for your Space:

### [poap](https://snapshot.org/#/strategy/poap)

The `poap` strategy returns the **balance** of POAP for a certain event as Voting power. However, when the `eventIds` is skipped, it will return the number of all POAP tokens owned by the address.

**Strategy setup:**

```
{
  "symbol": "POAP",
  "eventIds": [
    "1213",
    "1293"
  ]
}
```

:thinking: **How to find the event ID of the POAP?**&#x20;

Visit the POAP[ gallery](https://poap.gallery) and search for the name of the POAP you're looking for:

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-27 at 12.16.15.png" alt=""><figcaption></figcaption></figure>

You can test it out in the **Playground on Snapshot:**

{% embed url="https://snapshot.org/#/playground/poap?query=eyJwYXJhbXMiOnsic3ltYm9sIjoiUE9BUCIsImV2ZW50SWRzIjpbIjEyMTMiLCIxMjkzIl19LCJuZXR3b3JrIjoiMTAwIiwic25hcHNob3QiOiIiLCJhZGRyZXNzZXMiOlsiMHg4MzdkMjFjZmRhNzFlOTNlNTI1N2Y5NWNlMmM0OTc1MTY3NWViY2IxIiwiMHgwMGFjMzZjNTE1MDBlOTAwYWIwZjRlNjkyZmMxMzM4Y2Y3MDU3MWIyIiwiMHhkZDZmNzAyYzI5MDdjZTQwMTg4OGQ5OTNkN2RjMTg1ZTdhODI0NDY2Il19" %}

### [poap-with-weight](https://snapshot.org/#/strategy/poap-with-weight)

{% hint style="info" %}
It's suggested to use this strategy as an auxiliary scoring method because the score api server may have difficulty handling thousands of requests if huge single Ids are passed into the parameter.&#x20;
{% endhint %}

Since POAP is an ERC721 NFT, it can be distinguished by its tokenID, i.e. each tokenID represents a unique POAP. One can designate multiple tokenIDs and attach different weight to each.

In the example, if one holds a poap with the tokenID "100001", he will get 100 (1\*100) voting power. [Playground](https://snapshot.org/#/strategy/poap-with-weight)

```
{
  "symbol": "POAP",
  "tokenIds": [
    {"id":"100001", "weight": 100}, 
    {"id":"100002", "weight": 10}, 
    {"id":"1000", "weight": 1}
  ]
}
```
